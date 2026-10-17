---
description: >-
  Every meteo-houserobbery export a server owner would call - start and end a
  robbery in a house, read rooms and check if a player is on a job.
icon: code
---

# Exports

Start a house robbery from your own script (a mission, an event, a custom contract), check on it and end it. All exports are server side.

A **room** is one house built with the House Robbery creator, with its doors, loot props, loot zones and guards. Its id is the creator record id (a lowercase name like `mirror_park_bungalow`), which `GetRoomIds` lists.

The crime tablet job runs on top of these. Its own exports (`GetServiceDescriptor`, `StartService` and friends) are tablet plumbing and not listed here.

***

## Rooms

### GetRoomIds()

Every room that can be robbed right now.

```lua
for _, roomId in ipairs(exports['meteo-houserobbery']:GetRoomIds()) do
    print(roomId, exports['meteo-houserobbery']:GetRoomLabel(roomId))
end
--> mirror_park_bungalow   Mirror Park Bungalow
--> vinewood_hills_villa   Vinewood Hills Villa
```

### GetRoomLabel(roomId)

The room's name from the creator, or `nil`.

```lua
print(exports['meteo-houserobbery']:GetRoomLabel('mirror_park_bungalow')) --> Mirror Park Bungalow
```

### GetRoomEntrance(roomId)

Coords of the room's first door, for a blip or a GPS route. `nil` if the room does not exist.

```lua
local entrance = exports['meteo-houserobbery']:GetRoomEntrance('mirror_park_bungalow')
print(entrance.x, entrance.y, entrance.z) --> 1265.4   -458.1   70.5
```

***

## Robberies

### StartRobbery(roomId)

Opens a room for robbing: locks its doors and sets up its loot props, loot zones and guards (guards spawn when a door is opened). It runs until it is fully looted, times out (`Config.timeLimit`) or you end it.

```lua
local ok, err = exports['meteo-houserobbery']:StartRobbery('mirror_park_bungalow')
if not ok then
    print(err) --> already_active
end
```

Returns `true`, or `false` plus an error:

| Error | Meaning |
| ----- | ------- |
| `unknown_room` | No room with that id |
| `already_active` | The room is already being robbed |
| `no_doors` | The room has no doors set in the creator |

Starting a robbery this way does not hand out rewards, XP or cooldowns. That is the tablet job's part, so your script handles its own payout.

### EndRobbery(roomId, reason?)

Ends a robbery: removes the guards and clears the loot zone stashes. `reason` is a free text label for logs, `ended` by default.

```lua
exports['meteo-houserobbery']:EndRobbery('mirror_park_bungalow', 'mission_failed')
--> true    (false if no robbery was running there)
```

### IsRobberyActive(roomId)

```lua
print(exports['meteo-houserobbery']:IsRobberyActive('mirror_park_bungalow')) --> true
```

### IsRoomLooted(roomId)

`true` once every loot prop is taken and every loot zone stash is empty. The robbery ends by itself shortly after.

```lua
if exports['meteo-houserobbery']:IsRoomLooted('mirror_park_bungalow') then
    -- pay out your own mission reward
end
```

### Full example: a robbery for your own mission

```lua
local roomId = 'mirror_park_bungalow'

local ok, err = exports['meteo-houserobbery']:StartRobbery(roomId)
if not ok then return print('Could not start:', err) end

local entrance = exports['meteo-houserobbery']:GetRoomEntrance(roomId)
TriggerClientEvent('my-mission:client:setRoute', source, entrance)

CreateThread(function()
    while exports['meteo-houserobbery']:IsRobberyActive(roomId) do
        if exports['meteo-houserobbery']:IsRoomLooted(roomId) then
            QBCore.Functions.Notify(source, 'House cleared out', 'success')
            break
        end
        Wait(5000)
    end
end)
```

***

## Players

### IsPlayerInService(source)

`true` while the player is on a House Robbery job from the crime tablet.

```lua
if exports['meteo-houserobbery']:IsPlayerInService(source) then
    return QBCore.Functions.Notify(source, 'Finish your current job first', 'error')
end
```

### GetServiceCooldown(citizenid)

Seconds left before the player can take another tablet House Robbery job, `0` if none. Kept in memory, so a restart clears it.

```lua
print(exports['meteo-houserobbery']:GetServiceCooldown(citizenid)) --> 1260
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
