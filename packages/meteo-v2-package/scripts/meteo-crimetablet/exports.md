---
description: >-
  Every meteo-crimetablet export with a simple example and what it gives back -
  crypto, XP, reputation, crew groups, achievements and USB drives.
icon: code
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-crimetablet/exports.md
---

# Exports

Pay out crypto, hand out XP and use the tablet's crew groups from your own crime scripts. All exports are server side.

Progression is stored in the database with no cache, so XP and crypto work even when the player is offline.

***

## Player Data

### GetPlayerData(citizenid)

Full profile, or `nil` if they never set up a tablet.

```lua
local data = exports['meteo-crimetablet']:GetPlayerData(citizenid)
print(data.name, data.level, data.rank)
--> John Doe   7   Hustler
```

```lua
-- record:
{ name, walletAddress, balance, level, xp, reputation, rank }
```

### GetPlayerLevel(citizenid)

```lua
local level = exports['meteo-crimetablet']:GetPlayerLevel(citizenid)
print(level) --> 7    (0 if not found)
```

### GetCrimeProfile(citizenid)

Read-only snapshot, including how much XP the next level needs.

```lua
local p = exports['meteo-crimetablet']:GetCrimeProfile(citizenid)
print(p.level, p.xp, p.xpForNextLevel, p.rank)
--> 7   420   2861   Hustler
```

```lua
-- record:
{ name, balance, level, xp, xpForNextLevel, reputation, rank }  -- or nil
```

### AddXP(citizenid, amount)

Levels the player up automatically when they cross the threshold.

```lua
local result = exports['meteo-crimetablet']:AddXP(citizenid, 500)
print(result.level, result.xp, result.leveled)
--> 8   112   true
```

Returns `false` if the player has no tablet row.

### AddReputation(citizenid, amount)

Counts toward the `rep_100` achievement. `amount` must be above 0.

```lua
local ok = exports['meteo-crimetablet']:AddReputation(citizenid, 25)
print(ok) --> true
```

### AddRecentActivity(citizenid, text, icon?, color?)

Adds a line to the activity feed on their tablet dashboard.

```lua
exports['meteo-crimetablet']:AddRecentActivity(citizenid, 'Cracked a safe', 'lock_open', '#FF657A')
```

`icon` is a Material Icons name and defaults to `info`. `color` is a hex string and defaults to `#57EFAF`.

***

## Crypto and Wallet

### GetCryptoBalance(citizenid)

```lua
local balance = exports['meteo-crimetablet']:GetCryptoBalance(citizenid)
print(balance) --> 12500    (0 if not found)
```

### AddCrypto(citizenid, amount, reason?)

Logs a deposit transaction and an activity entry.

```lua
local ok = exports['meteo-crimetablet']:AddCrypto(citizenid, 1000, 'Heist payout')
print(ok) --> true
```

`reason` defaults to `External deposit`.

### RemoveCrypto(citizenid, amount, reason?)

Fails if the balance is too low, so use the return value as your "can they afford it" check.

```lua
local paid = exports['meteo-crimetablet']:RemoveCrypto(citizenid, 5000, 'Bought a blueprint')
if not paid then return end -- not enough balance
```

`reason` defaults to `External withdrawal`.

### GetWalletAddress(citizenid)

```lua
local wallet = exports['meteo-crimetablet']:GetWalletAddress(citizenid)
print(wallet) --> MTEO-KLL2-AIMT    (nil if not found)
```

### GetCitizenIdByWallet(wallet)

Reverse lookup.

```lua
local cid = exports['meteo-crimetablet']:GetCitizenIdByWallet('MTEO-KLL2-AIMT')
print(cid) --> ABC12345
```

### GetTransactionLogs(citizenid, limit?)

`limit` defaults to 20.

```lua
for _, tx in ipairs(exports['meteo-crimetablet']:GetTransactionLogs(citizenid, 10)) do
    print(tx.type, tx.amount, tx.description)
end
--> deposit    1000   Heist payout
--> withdraw   5000   Bought a blueprint
```

```lua
-- each entry:
{ type, amount, fee, description, from_wallet, to_wallet, created_at }
```

### PushBalance(source)

Pushes the current balance to their open tablet UI. Call it after `AddCrypto` or `RemoveCrypto` so you do not need to know the internal update event.

```lua
local balance = exports['meteo-crimetablet']:PushBalance(source)
print(balance) --> 13500
```

***

## Crew Groups

Run your activity for a whole crew and lock them out of other jobs while it runs.

### GetPlayerGroup(source)

```lua
local group = exports['meteo-crimetablet']:GetPlayerGroup(source)
print(group.name, #group.members, group.busy)
--> The Crew   3   false
```

```lua
-- group:
{
    id         = 'grp_A7F3',
    name       = 'The Crew',
    leader     = 12,          -- server id of the leader
    members    = { ... },
    busy       = false,
    task       = nil,         -- name of the activity holding them
    maxMembers = 4,
    createdAt  = 1751130000,
}

-- each member:
{ source = 12, citizenid = 'ABC12345', name = 'John Doe', role = 'leader', ready = true, profileImage = '' }
```

Returns `nil` if they are not in a group.

### IsPlayerInGroup(source)

```lua
print(exports['meteo-crimetablet']:IsPlayerInGroup(source)) --> true
```

### IsPlayerBusy(source)

True while their group is locked into another activity. `false` if they have no group.

```lua
if exports['meteo-crimetablet']:IsPlayerBusy(source) then return end
```

### IsPlayerGroupLeader(source)

```lua
print(exports['meteo-crimetablet']:IsPlayerGroupLeader(source)) --> true
```

### GetGroupById(groupId)

```lua
local group = exports['meteo-crimetablet']:GetGroupById('grp_A7F3')
```

### GetGroupMembers(groupId)

Empty table if the group is gone.

```lua
for _, m in ipairs(exports['meteo-crimetablet']:GetGroupMembers(groupId)) do
    print(m.name, m.citizenid, m.role)
end
--> John Doe    ABC12345   leader
--> Jane Roe    QWE45612   member
```

### SetGroupBusy(groupId, busy, taskName)

Locks the group so they cannot start another activity. Notifies every member.

```lua
exports['meteo-crimetablet']:SetGroupBusy(groupId, true, 'Warehouse job')
--> every member gets a "locked" notification
```

### ClearGroupTask(groupId)

Unlocks them. Always call this when your activity ends, including on failure.

```lua
exports['meteo-crimetablet']:ClearGroupTask(groupId)
```

### NotifyGroup(groupId, message, type?)

Notifies every member at once. `type` defaults to `primary`.

```lua
exports['meteo-crimetablet']:NotifyGroup(groupId, 'The truck is on the move', 'success')
```

### DisbandGroup(groupId)

```lua
exports['meteo-crimetablet']:DisbandGroup(groupId)
```

All four mutations return `true`, or `false` if the group id does not exist.

### Full example: run a job for a crew

```lua
if exports['meteo-crimetablet']:IsPlayerBusy(source) then return end

local group = exports['meteo-crimetablet']:GetPlayerGroup(source)
if not group then return end

exports['meteo-crimetablet']:SetGroupBusy(group.id, true, 'Warehouse job')

-- ... run the job ...

for _, member in ipairs(group.members) do
    exports['meteo-crimetablet']:AddCrypto(member.citizenid, 2500, 'Warehouse job')
    exports['meteo-crimetablet']:AddXP(member.citizenid, 400)
    exports['meteo-crimetablet']:PushBalance(member.source)
end

exports['meteo-crimetablet']:NotifyGroup(group.id, 'Payout sent', 'success')
exports['meteo-crimetablet']:ClearGroupTask(group.id)
```

***

## Achievements

Rewards are not handed out automatically. The player has to click Collect in the tablet.

### GetAchievementProgress(citizenid, achievementId)

```lua
local prog = exports['meteo-crimetablet']:GetAchievementProgress(citizenid, 'first_boost')
print(prog.progress, prog.completed, prog.collected)
--> 1   true   false
```

Never returns nil - an untouched achievement comes back as `{ progress = 0, completed = false, collected = false }`.

### UpdateAchievement(citizenid, achievementId, progress)

Sets progress to an exact value. Use it for threshold achievements like "hold 10k crypto" or "reach level 5".

```lua
local r = exports['meteo-crimetablet']:UpdateAchievement(citizenid, 'crypto_holder', 15000)
print(r.progress, r.completed) --> 15000   true
```

### IncrementAchievement(citizenid, achievementId, amount?)

Adds to the current progress. Use it for cumulative achievements. `amount` defaults to 1.

```lua
exports['meteo-crimetablet']:IncrementAchievement(citizenid, 'market_buyer')
local r = exports['meteo-crimetablet']:IncrementAchievement(citizenid, 'boost_earner', 500)
print(r.progress, r.completed) --> 500   false
```

Both return `false` if the achievement id is unknown.

### Achievement ids

General ones live in `meteo-crimetablet/shared/achievements.lua`:

`first_setup`, `crypto_starter`, `crypto_holder`, `crypto_whale`, `money_mover`, `market_buyer`, `market_seller`, `market_mogul`, `level_5`, `level_10`, `level_25`, `rep_100`

Boosting ones live in `meteo-boosting/shared/achievements.lua`:

`first_boost`, `boost_veteran`, `boost_expert`, `boost_legend`, `boost_level_3`, `boost_level_5`, `boost_level_10`, `group_booster`, `boost_trader`, `boost_earner`

***

## USB Drives

USB data lives in a shared table, so any player holding the item can interact with it.

### CreateUSB(source, data)

Creates a USB and gives it to the player. Returns the serial.

```lua
local serial = exports['meteo-crimetablet']:CreateUSB(source, {
    label      = 'Stolen Bank Records',
    type       = 'encrypted',
    difficulty = 'hard',
    content    = 'Account #847291...',
    reward     = {
        type    = 'file',
        name    = 'bank_records.dat',
        content = 'Transfers to a shell company in Vinewood',
    },
    expiresIn  = 3600,  -- optional, seconds. nil = never expires
})

print(serial) --> usb_A7F3B2    (nil on failure)
```

**Types**

| Type | How the player opens it |
| ---- | ----------------------- |
| `encrypted` | Typing minigame, difficulty sets the rounds and speed |
| `readable` | Content read straight from the terminal with `cat`, no minigame |
| `locked` | Needs a password via `unlock <serial> <password>` |

**Difficulty presets**

| Preset | Rounds | Code length | Time per round |
| ------ | ------ | ----------- | -------------- |
| `easy` | 2 | 4 chars | 12s |
| `medium` | 4 | 6 chars | 8s |
| `hard` | 6 | 8 chars | 6s |

Or pass your own table:

```lua
difficulty = { rounds = 3, codeLength = 5, timePerRound = 10 }
```

**Reward types** are `file` (saved to the player's tablet storage) or `item` (given to their inventory).

A readable USB needs no reward, since the content is the payload:

```lua
local serial = exports['meteo-crimetablet']:CreateUSB(source, {
    label   = 'Intel Report',
    type    = 'readable',
    content = 'Target: Fleeca on Route 68\nGuards: 2 armed\nWindow: 14:00-16:00',
})
```

### GetUSBData(serial)

```lua
local data = exports['meteo-crimetablet']:GetUSBData(serial)
print(data.label, data.type, data.status)
--> Stolen Bank Records   encrypted   active
```

```lua
-- record:
{ serial, label, type, difficulty, status, content, rewardType, expiresAt, createdAt, sourceResource }
-- or nil
```

### IsUSBValid(serial)

Exists, and not expired or already decrypted.

```lua
print(exports['meteo-crimetablet']:IsUSBValid(serial)) --> true
```

### ExpireUSB(serial)

Kill a USB when the mission fails or time runs out.

```lua
local ok = exports['meteo-crimetablet']:ExpireUSB(serial)
print(ok) --> true
```

### GetPlayerUSBs(source)

Every active USB in their inventory, with the stored data.

```lua
for _, u in ipairs(exports['meteo-crimetablet']:GetPlayerUSBs(source)) do
    print(u.serial, u.label, u.type, u.status)
end
--> usb_A7F3B2   Stolen Bank Records   encrypted   active
```

***

## Organizations

### AddOrgLog(orgId, text, icon?, color?)

Adds a line to an organization's log feed.

```lua
exports['meteo-crimetablet']:AddOrgLog(orgId, 'Sold 20 packages', 'sell', '#57EFAF')
```

`icon` defaults to `info`, `color` to `#9B6DFF`.

### AddServiceOrgXP(citizenid, amount)

Awards org XP to whichever organization the player belongs to. Does nothing if they have no org, or the organizations resource is not running.

```lua
local ok = exports['meteo-crimetablet']:AddServiceOrgXP(citizenid, 100)
print(ok) --> true
```

***

## Blackmarket Services

Register your own resource as a blackmarket service so it shows up in the tablet. Your resource must export `GetServiceDescriptor()` returning the service table.

### RegisterService(serviceId, resourceName)

```lua
exports['meteo-crimetablet']:RegisterService('my-service', GetCurrentResourceName())
--> true
```

### UnregisterService(serviceId)

Called for you when your resource stops, so you rarely need it.

```lua
exports['meteo-crimetablet']:UnregisterService('my-service')
```

***

## Misc

### GetTabletName(citizenid)

```lua
local name = exports['meteo-crimetablet']:GetTabletName(citizenid)
print(name) --> Ghost    (nil if they never set one up)
```

### GetOnDutyPoliceCount()

```lua
local cops = exports['meteo-crimetablet']:GetOnDutyPoliceCount()
print(cops) --> 4

if cops < 3 then
    return TriggerClientEvent('ox_lib:notify', source, { type = 'error', description = 'Too quiet out there, try later' })
end
```
