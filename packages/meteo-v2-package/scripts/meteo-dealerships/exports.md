---
description: >-
  Every meteo-dealerships export with a simple example and what it gives back -
  financed vehicles, dealerships, employees, roles, permissions and test drives.
icon: code
---

# Exports

Check vehicle finance, read dealerships and their staff, and gate your own scripts on a dealership permission.

`dealerId` is the dealership's key, e.g. `'pdm'`. Server reads come straight from memory, so they are cheap to call.

***

## Server: Finance

### isVehicleFinanced(plate)

The one to call before letting a player sell, scrap or transfer a car. The plate is trimmed for you.

```lua
local result = exports['meteo-dealerships']:isVehicleFinanced(plate)

if result.financed then
    print('Still owes $' .. result.data.balanceRemaining)
    return -- block the sale
end
```

Returns `{ financed = true, data = financeData }` or `{ financed = false, data = nil }`.

```lua
-- financeData:
{
    dealership        = 'pdm',
    buyerCitizenid    = 'ABC12345',
    originalPrice     = 150000,
    downPayment       = 15000,
    totalFinanced     = 135000,     -- price minus down payment
    interestRate      = 10,         -- percent
    totalWithInterest = 148500,
    monthlyPayment    = 12375,
    paymentsTotal     = 12,
    paymentsMade      = 4,
    paymentsRemaining = 8,
    balanceRemaining  = 99000,
    nextPaymentDue    = 1782400000, -- unix seconds
    purchasedAt       = 1782000000,
    lastPaymentAt     = 1782300000, -- nil before the first payment
    missedPayments    = 0,
    warningIssued     = false,
}
```

### getVehicleFinanceData(plate)

Same `financeData` table, or `nil` if the vehicle is not financed.

```lua
local data = exports['meteo-dealerships']:getVehicleFinanceData(plate)
if data then print(data.paymentsRemaining) end --> 8
```

### isVehicleOverdue(plate)

`true` once the next payment is past due. `false` if it is not financed.

```lua
if exports['meteo-dealerships']:isVehicleOverdue(plate) then
    -- flag it for the repo job
end
```

***

## Server: Dealerships and Vehicles

### getDealership(dealerId)

```lua
local dealer = exports['meteo-dealerships']:getDealership('pdm')
print(dealer.label, dealer.type, dealer.owner) --> Premium Deluxe Motorsport   owned   ABC12345
```

```lua
-- record:
{
    id       = 'pdm',
    label    = 'Premium Deluxe Motorsport',
    type     = 'owned',     -- the dealership mode from config, or 'removed'
    owner    = 'ABC12345',  -- citizenid, nil if unowned
    balance  = 250000,
    settings = { ... },
    config   = { ... },     -- the dealership's config entry
    active   = true,        -- false once removed from config
}
```

### getAllDealerships()

Every dealership, keyed by `dealerId`.

```lua
for id, dealer in pairs(exports['meteo-dealerships']:getAllDealerships()) do
    print(id, dealer.label)
end
```

### getVehicle(model)

A vehicle from the dealership catalogue, or `nil`.

```lua
local veh = exports['meteo-dealerships']:getVehicle('sultan')
print(veh.name, veh.brand, veh.basePrice) --> Sultan   Karin   45000
```

```lua
-- record:
{
    model = 'sultan', name = 'Sultan', brand = 'Karin', category = 'sports',
    customclass = 'B', basePrice = 45000,
    priceOverrides = { ... }, shops = { 'pdm' },
    featured = false, available = true,
}
```

***

## Server: Employees and Permissions

Only owned dealerships have employees. The owner always passes every check, even without an employee row.

### isEmployee(dealerId, citizenid) / isOwner(dealerId, citizenid)

```lua
local cid = player.PlayerData.citizenid
print(exports['meteo-dealerships']:isEmployee('pdm', cid)) --> true
print(exports['meteo-dealerships']:isOwner('pdm', cid))    --> false
```

### hasPermission(dealerId, citizenid, permission)

```lua
if exports['meteo-dealerships']:hasPermission('pdm', cid, 'sellVehicle') then
    -- let them use your sales tool
end
```

| Group | Permissions |
| ----- | ----------- |
| View | `viewInventory`, `viewSales`, `viewLogs`, `viewFinances`, `viewCustomers`, `viewRepos` |
| Sales | `sellVehicle`, `testDrive` |
| Stock | `editPrices`, `orderVehicles`, `setFeatured`, `manageLTO`, `manageDisplay` |
| Team | `hireEmployees`, `fireEmployees`, `manageApplications`, `manageQuestions` |
| Money | `deposit`, `withdraw` |
| Extra | `announce` |

### getEmployee(dealerId, citizenid)

The employee row, or `nil`. The owner is not returned here unless they were also hired.

```lua
local emp = exports['meteo-dealerships']:getEmployee('pdm', cid)
--> { citizenid = 'ABC12345', grade = 2, hiredAt = ..., commissionEarned = 12000, pendingCommission = 800 }
```

### getDealershipEmployees(dealerId)

Every employee, keyed by citizenid. Empty table if none.

```lua
for cid, emp in pairs(exports['meteo-dealerships']:getDealershipEmployees('pdm')) do
    print(cid, emp.grade)
end
```

### getEmployeeRole(dealerId, citizenid)

The role a player holds, owner included. `nil` if they hold none.

```lua
local role = exports['meteo-dealerships']:getEmployeeRole('pdm', cid)
print(role.label, role.commission, role.isOwner) --> Sales Associate   10   false
```

```lua
{ grade = 2, label = 'Sales Associate', paycheck = 500, commission = 10, permissions = { sellVehicle = true, ... }, isOwner = false }
```

The owner comes back as grade `100` with every permission.

### getDealershipGrades(dealerId)

Every role the dealership has, lowest first, with the owner last.

```lua
for _, g in ipairs(exports['meteo-dealerships']:getDealershipGrades('pdm')) do
    print(g.grade, g.name, g.isboss)
end
--> 1     Trainee           false
--> 2     Sales Associate   false
--> 100   Owner             true
```

### getPlayerEmployments(citizenid)

Every dealership a player works at or owns, keyed by `dealerId`.

```lua
for id, e in pairs(exports['meteo-dealerships']:getPlayerEmployments(cid)) do
    print(id, e.dealershipName, e.gradeLabel, e.isOwner)
end
--> pdm   Premium Deluxe Motorsport   Owner   true
```

```lua
-- each entry:
{ dealershipId, dealershipName, grade, gradeLabel, permissions, hiredAt, isOwner }
```

***

## Client

Client checks read the local player's synced data. They are for showing or hiding things in your own UI - the server still validates every action.

### isEmployee(dealerId) / isOwner(dealerId) / canManage(dealerId)

`canManage` is true for any employee or the owner.

```lua
if exports['meteo-dealerships']:canManage('pdm') then
    -- show your extra option
end
```

### hasPermission(dealerId, permission)

Same permission keys as the server.

```lua
print(exports['meteo-dealerships']:hasPermission('pdm', 'testDrive')) --> true
```

### getGrade(dealerId)

The player's grade there, or `nil`.

```lua
print(exports['meteo-dealerships']:getGrade('pdm')) --> 2
```

### getEmployment(dealerId) / getAllEmployments()

The same entries as the server's `getPlayerEmployments`, for the local player.

```lua
local e = exports['meteo-dealerships']:getEmployment('pdm')
if e then print(e.gradeLabel) end
```

### getDealership(dealerId)

The client copy of a dealership, or `nil`.

```lua
local dealer = exports['meteo-dealerships']:getDealership('pdm')
```

### isUIOpen() / getCurrentUI()

Is a dealership screen open, and which one. Handy to stop your own keybinds firing over it.

```lua
if exports['meteo-dealerships']:isUIOpen() then return end
```

### isOnTestDrive() / getTestDriveTimeRemaining()

`getTestDriveTimeRemaining` is in seconds, `0` when not on a test drive.

```lua
if exports['meteo-dealerships']:isOnTestDrive() then
    print(exports['meteo-dealerships']:getTestDriveTimeRemaining()) --> 95
end
```
