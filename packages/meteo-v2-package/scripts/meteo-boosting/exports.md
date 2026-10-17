---
description: >-
  Every meteo-boosting export a server owner would call - hand out contracts,
  read boosting levels, contracts, active boosts and cooldowns.
icon: code
---

# Exports

Give boosting contracts from your own scripts (a shop, a reward, a mission) and read a player's boosting level, contracts and cooldown. All exports are server side.

Starting, cancelling, transferring and selling contracts runs through the crime tablet, which calls its own set of exports on this script. Those are not listed here.

***

## Contracts

### CreateContract(source, class)

Creates a contract of a class and gives the player the contract item. Vehicle, reward and XP are rolled from the class config.

```lua
local serial = exports['meteo-boosting']:CreateContract(source, 'C')
print(serial) --> C-4F7A21    (false on failure)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `source` | number | Player server id |
| `class` | string | A key from `Config.classes`: `D`, `C`, `A` or `S` by default. Defaults to `D` |

Returns `false` if the player is not loaded, the class does not exist or the item could not be added (full inventory). The player gets a notification on success.

The contract sits in their inventory until they use the item, then it shows up in their tablet.

### GetPlayerContracts(citizenid)

Every contract a player owns, newest first, including finished and cancelled ones.

```lua
for _, c in ipairs(exports['meteo-boosting']:GetPlayerContracts(citizenid)) do
    print(c.serial, c.class, c.vehicle_label, c.status)
end
--> C-4F7A21   C   Sultan   available
```

```lua
-- each contract (database row plus class info):
{
    serial, citizenid, class, vehicle, vehicle_label, reward, xp_reward,
    status,          -- 'inventory', 'available', 'active', 'listed', 'cancelled' and so on
    listed_price, created_at,
    level_required,  -- from the class config
    class_tag,       -- e.g. 'EASY'
    steps,           -- the class steps
}
```

### GetContractData(serial)

One contract's database row, or `nil`.

```lua
local c = exports['meteo-boosting']:GetContractData('C-4F7A21')
print(c.citizenid, c.status, c.reward) --> ABC12345   available   210
```

### GetClassConfig(class)

The config for one class, or `nil`.

```lua
local class = exports['meteo-boosting']:GetClassConfig('S')
print(class.label, class.levelRequired) --> S Class   9
```

***

## Players

### GetBoostingLevel(citizenid)

The player's boosting level and XP.

```lua
local lvl = exports['meteo-boosting']:GetBoostingLevel(citizenid)
print(lvl.level, lvl.name, lvl.xp, lvl.nextXP)
--> 2   Wheelman   980   1400
```

```lua
-- record:
{ level, name, xp, nextXP }   -- nextXP is nil at max level
```

### GetActiveBoost(source)

The boost a player is running as the leader (or solo), or `nil`.

```lua
local boost = exports['meteo-boosting']:GetActiveBoost(source)
if boost then
    print(boost.serial, boost.class, boost.vehicleLabel, boost.step)
end
--> C-4F7A21   C   Sultan   2
```

```lua
-- main fields:
{
    serial, citizenid, class, vehicle, vehicleLabel,
    reward, xpReward, repReward,
    step, totalSteps,
    vehicleNetId,     -- nil until the car spawns
    groupId,          -- nil for a solo boost
    groupMembers,     -- { { source, citizenid } } or nil
    vinScratch,
}
```

### GetActiveBoostForMember(source)

For a group member who is not the leader, the boost their group is running. `nil` otherwise.

```lua
local boost = exports['meteo-boosting']:GetActiveBoost(source)
    or exports['meteo-boosting']:GetActiveBoostForMember(source)

if boost then
    return QBCore.Functions.Notify(source, 'Finish your boost first', 'error')
end
```

***

## Cooldowns

After a boost ends, every player in it gets a cooldown (`Config.cooldown`). It is kept in memory, so a restart clears it.

### GetBoostCooldown(citizenid)

Seconds left on the player's cooldown, `0` if none.

```lua
local remaining = exports['meteo-boosting']:GetBoostCooldown(citizenid)
print(remaining) --> 540
```

### ResetBoostCooldown(citizenid)

Clears the cooldown.

```lua
exports['meteo-boosting']:ResetBoostCooldown(citizenid)
```

### GetBoostingStatus(citizenid)

Cooldown status in one table.

```lua
local status = exports['meteo-boosting']:GetBoostingStatus(citizenid)
print(status.onCooldown, status.remaining, status.cooldownDuration)
--> true   540   1800
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
