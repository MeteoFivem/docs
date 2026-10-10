---
description: >-
  Every meteo-misc export with a simple example - check a vehicle boot and put
  a player in it from your own script.
icon: code
---

# Exports

Use the vehicle trunk (boot) feature from your own scripts, for example a kidnapping or a "put in trunk" option on your own escort system. meteo-policejob uses the same exports for its put in trunk option.

***

## Client

### CanPutInTrunk(vehicle)

Can the calling player put someone in this vehicle's boot right now?

```lua
-- vehicle = the vehicle entity your target option is on
if exports['meteo-misc']:CanPutInTrunk(vehicle) then
    -- show your "Put in trunk" option
end
```

`true` only when all of these are true:

* The player is not already in a trunk
* The vehicle has a working boot and its class or model is not blocked in the config
* The vehicle is unlocked and the boot is open (or the lid is gone)
* Nobody is in the boot
* The player is standing at the boot (`Config.trunkInteractDistance`)

### AttachIntoTrunk(netId)

Puts the **calling** player into the boot of the vehicle. Run it on the client of the player going in, after the server has reserved the boot with `ReserveTrunkFor`.

```lua
RegisterNetEvent('myscript:client:putInTrunk', function(netId)
    local ok = exports['meteo-misc']:AttachIntoTrunk(netId)
    if not ok then
        -- free the reserved boot again
        TriggerServerEvent('meteo-misc:server:releaseTrunk')
    end
end)
```

Returns `false` if the player is dead, cuffed or knocked out, already in a vehicle or trunk, or the vehicle has no boot bone. The player can climb out on their own as usual.

***

## Server

### ReserveTrunkFor(targetSrc, netId)

Reserves the boot for another player. Call it first, then tell that player's client to run `AttachIntoTrunk`.

```lua
local reserved = exports['meteo-misc']:ReserveTrunkFor(targetId, netId)
if not reserved then
    return QBCore.Functions.Notify(source, 'The trunk is taken', 'error')
end

TriggerClientEvent('myscript:client:putInTrunk', targetId, netId)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `targetSrc` | number | Server id of the player going in |
| `netId` | number | Network id of the vehicle |

Returns `false` if the target is dead, cuffed or knocked out, is not near the vehicle, or someone else is already in the boot. A player can hold one boot at a time, so reserving a new one frees their old one.

Your own script still has to check the player calling it is allowed to do this (distance, job, escort).

### Who is in the boot

The occupant's server id is on the vehicle statebag, readable on both sides.

```lua
local occupant = Entity(vehicle).state.meteoTrunk
print(occupant) --> 12   (nil when empty)
```
