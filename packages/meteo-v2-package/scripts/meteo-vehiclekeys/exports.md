---
description: >-
  Every meteo-vehiclekeys export with a simple example and what it gives back -
  give, remove and check keys, lock state, performance class and job shared keys.
icon: code
---

# Exports

Give and take keys, check who has them and lock vehicles from your own scripts.

Every key export accepts either a vehicle entity or a plate string. A plate matches every spawned vehicle with that plate.

***

## Server: Keys

### GiveKeys(source, vehicle | plate?, skipNotification?)

Gives a player keys to a vehicle. Leave `vehicle` out to use the vehicle the player is sitting in.

```lua
local ok = exports['meteo-vehiclekeys']:GiveKeys(source, vehicle)
print(ok) --> true

exports['meteo-vehiclekeys']:GiveKeys(source, 'ABC 123', true) -- by plate, no notification
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `source` | number | Server id |
| `vehicle` | number / string / nil | Entity, plate, or `nil` for their current vehicle |
| `skipNotification` | boolean | `true` hides the "you got the keys" notification |

Returns `true` if keys were given to at least one vehicle (or they already had them), `false` if no vehicle was found.

{% hint style="info" %}
A plate for a vehicle that was spawned a moment ago may not be known to the server yet. The export retries once after 500ms before giving up.
{% endhint %}

### RemoveKeys(source, vehicle | plate?, skipNotification?)

Takes keys away. Same arguments as `GiveKeys`.

```lua
local ok = exports['meteo-vehiclekeys']:RemoveKeys(source, vehicle)
print(ok) --> true    (false if they did not have keys)
```

### HasKeys(source, vehicle | plate?)

```lua
if exports['meteo-vehiclekeys']:HasKeys(source, vehicle) then
    -- let them start the engine
end
```

The owner of a garage vehicle always has keys, even after a relog or restart.

### SetLockState(vehicle, state)

Locks or unlocks a vehicle for everyone.

```lua
exports['meteo-vehiclekeys']:SetLockState(vehicle, 'lock')
exports['meteo-vehiclekeys']:SetLockState(vehicle, 'unlock')
```

`state` is `'lock'` / `'unlock'`, or `2` / `1`. Anything else is ignored. Takes an entity, not a plate.

***

## Server and Client: Performance Class

### GetPerformanceClass(model)

The vehicle's performance class, which sets the lockpick difficulty. Works on both sides.

```lua
local class = exports['meteo-vehiclekeys']:GetPerformanceClass('zentorno')
print(class) --> S
```

`model` is a spawn name or a model hash. Classes come from `Config.classRules` (`S`, `A`, `B`, `C`, `D`, `E` by default).

***

## Client

### HasKeys(vehicle | plate?)

Does the local player have keys. Leave it empty to check the vehicle they are in.

```lua
if exports['meteo-vehiclekeys']:HasKeys() then
    print('keys for this car')
end

print(exports['meteo-vehiclekeys']:HasKeys('ABC 123')) --> false
```

### AddSharedKeys(job, models, opts?)

Lets everyone in a job use a set of vehicle models without their own keys, on top of `Config.sharedKeys`. Call it on the client at start-up.

```lua
exports['meteo-vehiclekeys']:AddSharedKeys('police', { 'police3', 'policeb' }, {
    autolock = false,     -- optional, default false
    onDutyOnly = true,    -- optional, default true
})
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `job` | string | Job name |
| `models` | table | Spawn names or hashes |
| `opts` | table | Only used on the first call for a job, unless you pass it again |

***

## Statebags

All key state lives in replicated statebags, so you can also read it directly without an export.

```lua
Player(source).state.keysList        -- [sessionId] = true
Entity(vehicle).state.sessionId      -- the vehicle's key id
Entity(vehicle).state.owner          -- citizenid of the owner, for garage vehicles
Entity(vehicle).state.doorslockstate -- 1 = unlocked, 2 = locked
```

***

## Compatibility

meteo-vehiclekeys provides `qbx_vehiclekeys` and `qb-vehiclekeys`, so scripts written for either keep working without changes.

| Exports | Side |
| ------- | ---- |
| `GiveKeys`, `RemoveKeys`, `HasKeys`, `SetLockState` | Server |
| `HasKeys` | Client |

```lua
exports['qbx_vehiclekeys']:GiveKeys(source, vehicle)
exports['qb-vehiclekeys']:HasKeys('ABC 123')
```

The old qb-vehiclekeys events also still work:

```lua
-- client
TriggerEvent('vehiclekeys:client:SetOwner', plate)
TriggerEvent('qb-vehiclekeys:client:AddKeys', plate)
TriggerEvent('qb-vehiclekeys:client:RemoveKeys', plate)
```

A plate sent through these events only gives keys to a vehicle close to the player.

Do not run qbx_vehiclekeys or qb-vehiclekeys next to meteo-vehiclekeys.
