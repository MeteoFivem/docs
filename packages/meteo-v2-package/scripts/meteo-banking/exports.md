---
description: >-
  Every meteo-banking export with a simple example and what it gives back -
  balances, adding and removing money, transfers, history, bills, taxes and
  business accounts.
icon: code
---

# Exports

Move money and read accounts from your own scripts. Every export is server side, and every call is logged with the resource that made it, so all money flows show up in the bank history.

***

## Account refs

Every export that takes a `ref` accepts any of these:

| Ref | Means |
| --- | ----- |
| `source` (number) | That player's bank (the core bank money) |
| `'ABC12345'` | A citizenid. The player's bank, works offline |
| `'job:police'` / `'gang:ballas'` | Job or gang account. Created on first use if the job or gang exists |
| `'police'` | Job or gang account, but only if it already exists. Use `job:` to be safe |
| `'482913'` | Account number |
| `{ id = 5 }`, `{ number = '482913' }`, `{ job = 'police' }`, `{ gang = 'ballas' }`, `{ citizenid = 'ABC12345' }`, `{ source = 1 }` | Table form |
| `{ business = 'restaurant', id = '3' }` / `'biz:restaurant:3'` | Business account (see [Business accounts](#business-accounts)) |

## Transaction details

Most money exports take an optional `tx` table as the last argument. It is what shows up in the bank history.

```lua
{
    category     = 'fuel',          -- deposit withdraw payment payroll sale fine purchase interest invoice rent fuel tax other
    title        = 'LTD Gasoline',
    description  = '42 L premium',
    counterparty = 'LTD Grove St',
    actor        = source,          -- server id or citizenid of who did it
    actorName    = 'John Doe',      -- optional, filled in from actor when it is a server id
    location     = 'Grove Street',
    metadata     = { plate = 'KRX220' },
    tag          = 'sale_cash',     -- your own row type, filter on it in GetTransactions
    allowNegative = false,          -- true lets RemoveMoney overdraw
    tax          = 21,              -- optional tax inside this amount, shown as a breakdown
    taxRate      = 5,
    taxKind      = 'fuel',
    taxMode      = 'added',         -- 'added' (paid on top, default) or 'deducted'
}
```

A plain string instead of a table is used as the description, like qb-banking.

Errors the money exports can return: `invalid_amount`, `account_not_found`, `insufficient_funds`, `account_frozen`, `account_closed`, `same_account`, `core_refused`, `not_ready`.

***

## Money

### AddMoney(ref, amount, tx?)

Returns `ok, err`.

```lua
local ok, err = exports['meteo-banking']:AddMoney(source, 500, {
    category = 'sale',
    title = 'Sold fish',
    actor = source,
})
print(ok, err) --> true  nil
```

### RemoveMoney(ref, amount, tx?)

Returns `ok, err`. Fails with `insufficient_funds` when the account cannot cover it, unless `tx.allowNegative = true`.

```lua
local ok, err = exports['meteo-banking']:RemoveMoney(source, 120, {
    category = 'fuel',
    title = 'LTD Gasoline',
    description = '42 L',
    actor = source,
})

if not ok then
    print(err) --> insufficient_funds
end
```

### Transfer(fromRef, toRef, amount, tx?)

Moves money between two accounts in one step. Returns `ok, err`.

```lua
-- paycheck from the society
local ok, err = exports['meteo-banking']:Transfer('job:police', source, 3400, {
    category = 'payroll',
    title = 'Paycheck',
})
```

### LogTransaction(ref, signedAmount, tx?)

Writes a history row without moving any money. Use it when the money already moved somewhere else. Negative is money out. Returns `ok`.

```lua
exports['meteo-banking']:LogTransaction('job:mechanic', -2500, {
    category = 'purchase',
    title = 'Parts order',
})
```

***

## Reading Accounts

### GetBalance(ref)

The balance, or `nil` if the account does not exist.

```lua
local balance = exports['meteo-banking']:GetBalance('job:police')
print(balance) --> 184200
```

### CanAfford(ref, amount)

```lua
if exports['meteo-banking']:CanAfford(source, 5000) then
    -- go ahead
end
```

### GetAccountInfo(ref)

```lua
local info = exports['meteo-banking']:GetAccountInfo('job:police')
print(json.encode(info))
```

```lua
{
    id = 12,
    type = 'job',          -- player | job | gang | personal | business
    owner = 'police',
    name = 'Los Santos Police',
    number = '482913',
    balance = 184200,
    frozen = false,
    closed = false,
}
```

### GetTransactions(ref, limit?, beforeId?)

Newest first. `limit` defaults to 50 and caps at 500. Pass the last row's `id` as `beforeId` to load the next batch.

```lua
for _, row in ipairs(exports['meteo-banking']:GetTransactions(source, 10)) do
    print(row.title, row.amount, row.balance_after)
end
--> Paycheck     3400   12400
--> LTD Gasoline -120   9000
```

Each row: `id`, `category`, `amount` (negative is money out), `balance_after`, `title`, `description`, `counterparty`, `actor`, `actor_name`, `resource`, `location`, `created_at`.

### GetTransactions(ref, opts)

The paged version. `opts = { page?, perPage?, search?, tags? }`. `perPage` defaults to 20 and caps at 100.

```lua
local page = exports['meteo-banking']:GetTransactions({ business = 'restaurant', id = '3' }, {
    page = 1,
    perPage = 25,
    search = 'burger',
    tags = { 'sale_cash', 'sale_card' },
})
print(page.total, page.pages) --> 64  3
```

Returns `{ rows, page, pages, total }`. Each row also carries its `tag` and `tax` breakdown.

### GetTransactionSummary(ref, since)

Totals per `tag` since a unix time.

```lua
local since = os.time() - 7 * 86400
for _, r in ipairs(exports['meteo-banking']:GetTransactionSummary('job:mechanic', since)) do
    print(r.tag, r.count, r.money_in, r.money_out)
end
--> repair   41   58200   0
--> parts    6    0       9100
```

### CreateSocietyAccount(kind, name, label?)

Makes sure a job or gang account exists. `kind` is `'job'` or `'gang'`. Returns the account id, or `nil`.

```lua
local id = exports['meteo-banking']:CreateSocietyAccount('job', 'taxi', 'Downtown Cab Co.')
print(id) --> 18
```

***

## Bills

A bill asks a player for money into an account (a player's bank, a job or a business). The player sees it on the phone and pays from an account or cash, or declines.

### CreateBill(data)

`data = { account = ref, target = source | citizenid, amount, reason?, sender? = source | citizenid, senderName? }`. Returns the bill id, or `nil, err`.

```lua
local billId, err = exports['meteo-banking']:CreateBill({
    account = 'job:ambulance',
    target  = targetSource,
    amount  = 750,
    reason  = 'Treatment at Pillbox',
    sender  = source,
})
print(billId, err) --> 214  nil
```

Errors: `account_not_found`, `target_not_found`, `invalid_amount`, `cannot_bill_self`, `too_many_bills` (25 open per player), `not_ready`.

### CancelBill(id)

Only while the bill is still pending. Returns `ok, err`.

```lua
local ok, err = exports['meteo-banking']:CancelBill(214)
```

Error: `bill_not_found`.

### GetBill(id)

```lua
local bill = exports['meteo-banking']:GetBill(214)
print(bill.status) --> pending
```

```lua
{
    id = 214, account = 7, accountName = 'Pillbox Medical',
    sender = 'XYZ98765', senderName = 'Dr. Vargas',
    target = 'ABC12345', targetName = 'John Doe',
    amount = 750, reason = 'Treatment at Pillbox',
    status = 'pending',   -- pending | paid | cancelled | declined
    createdAt = ..., closedAt = ...,
}
```

### Events

Server events, not net events.

```lua
AddEventHandler('meteo-banking:server:billCreated', function(bill) end)
AddEventHandler('meteo-banking:server:billClosed', function(bill)
    -- bill.status is 'paid', 'cancelled' or 'declined'
end)

-- a player's main account received a transfer
AddEventHandler('meteo-banking:server:moneyReceived', function(data)
    -- data = { citizenid, account, amount, from, note }
end)
```

***

## Taxes

Tax rates are set by the mayor in the meteo-mdt and paid into the tax job's account. Without the MDT, without a tax account or for an unknown kind, the rate is `0`, so a sale never fails because of tax.

### GetTaxRate(kind)

The rate in percent.

```lua
print(exports['meteo-banking']:GetTaxRate('fuel')) --> 5
```

### QuoteTax(kind, amount)

Whole-dollar tax on an amount. Returns `tax, rate`.

```lua
local tax, rate = exports['meteo-banking']:QuoteTax('shop_purchase', 1200)
print(tax, rate) --> 60  5
```

### PayTax(kind, amount, tx?)

Pays collected tax into the tax account. `tx = { title?, description?, counterparty?, actor? }`. Returns `true` or `false`.

```lua
local price = 1200
local tax = exports['meteo-banking']:QuoteTax('shop_purchase', price)

if exports['meteo-banking']:RemoveMoney(source, price + tax, { category = 'purchase', title = 'Hardware store', tax = tax, actor = source }) then
    exports['meteo-banking']:PayTax('shop_purchase', tax, { counterparty = 'Hardware store', actor = source })
end
```

***

## Business Accounts

For business scripts (restaurants, dealerships and so on) that want their money held in the bank. Banking keeps the balance and history, your script answers who may use it. Players see it in the bank under **Business accounts**.

### RegisterBusiness(kind, opts?)

Call it when your script starts and again on `meteo-banking:server:ready`. `kind` is lowercase letters, digits and `_`, max 16 characters. `opts = { label?, loans? }`. Returns `ok, err`.

```lua
local function register()
    if GetResourceState('meteo-banking') ~= 'started' then return end
    exports['meteo-banking']:RegisterBusiness('restaurant', { label = 'Restaurant' })
end

AddEventHandler('meteo-banking:server:ready', register)
CreateThread(register)
```

Your resource must export these before it registers, banking calls each one once to check:

| Export your script provides | Returns |
| --------------------------- | ------- |
| `BankingBusinessesFor(citizenid)` | `{ 'id1', 'id2' }` businesses this person may see |
| `BankingAccess(id, citizenid)` | `mask, role`. Bits: `view = 1`, `deposit = 2`, `withdraw = 4`, `transfer = 8`. Role is `'owner'` or `'staff'`. `0` = no access |
| `BankingLoansFor(citizenid)` | Only with `loans = true`. List of `{ id, title, subtitle, lender, balance, payment, paid, count, nextDue, missed, status }` |
| `BankingPayLoan(source, loanId, amount, accountRef)` | Only with `loans = true`. Charge with `RemoveMoney(accountRef, ...)` yourself and return `ok, err` |

Errors: `invalid_kind`, `kind_taken`, `missing_export`.

### SyncBusiness(kind, id, info)

Creates the account the first time (moving your balance in as the opening balance), then applies anything your script changed while banking was off. `info = { name, balance, synced }`, where `synced` is the balance banking last mirrored (`nil` on the first run).

```lua
local info = exports['meteo-banking']:SyncBusiness('restaurant', id, {
    name    = 'Burger Shot',
    balance = row.bank,
    synced  = row.bank_synced,
})
print(json.encode(info))
--> { "account": 12, "number": "512 774", "balance": 81200 }
```

Only the resource that registered the kind can sync or close it. Errors: `not_provider`, `invalid_id`.

### CloseBusiness(kind, id)

The business was deleted. The remaining balance is written off and the history stays. Syncing the same id again reopens it. Returns `ok, err`.

```lua
exports['meteo-banking']:CloseBusiness('restaurant', id)
```

### Moving business money

Use the normal money exports with a business ref.

```lua
local ref = { business = 'restaurant', id = tostring(restaurantId) }
exports['meteo-banking']:AddMoney(ref, 250, { category = 'sale', title = 'Counter order', tag = 'order', actor = source })
exports['meteo-banking']:Transfer(source, ref, 500, { title = 'Deposit', actor = source })
```

Banking fires this after every change, so you can mirror the balance into your own column:

```lua
AddEventHandler('meteo-banking:server:businessBalance', function(kind, id, balance)
    if kind ~= 'restaurant' then return end
    -- update your cache and your bank / bank_synced columns
end)
```

***

## Compatibility

Scripts written for these banking resources keep working with no changes. The calls land in meteo-banking.

| Resource | Exports |
| -------- | ------- |
| `qb-banking`, `qb-management` | `AddMoney`, `RemoveMoney`, `GetAccount`, `GetAccountBalance` |
| `Renewed-Banking` | `getAccountMoney`, `addAccountMoney`, `removeAccountMoney`, `handleTransaction`, `getAccountTransactions`, `GetJobAccount`, `CreateJobAccount` |

`GetAccount(name)` and `GetAccountBalance(name)` return the balance, or `0` if the account does not exist.

Scripts that change bank money straight through the core (`Player.Functions.AddMoney('bank', ...)`) are still logged, as category `other` with the core's reason.
