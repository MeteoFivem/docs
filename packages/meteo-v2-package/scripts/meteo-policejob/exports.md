---
description: >-
  Every meteo-policejob export with a simple example and what it gives back -
  handcuffs, ankle cuffs, escorting, headbags and shields.
icon: code
---

# Exports

Check whether a player is cuffed, escorted, bagged or holding a shield before your own script lets them do something.

All exports are client side and read the calling player. For a server-side cuff check, see [Reading cuff state on the server](#reading-cuff-state-on-the-server).

***

## Cuffs

### IsHandcuffed()

```lua
if exports['meteo-policejob']:IsHandcuffed() then
    return -- can't open the phone while cuffed
end
```

### HasAnkleCuff()

True while the player wears ankle cuffs, which slow their walk.

```lua
print(exports['meteo-policejob']:HasAnkleCuff()) --> false
```

### Reading cuff state on the server

Handcuffs are also saved to the player metadata.

```lua
local player = exports.qbx_core:GetPlayer(src)
print(player.PlayerData.metadata.ishandcuffed) --> true
```

***

## Escort

Ids are server ids.

### IsEscorted()

True while someone is escorting this player.

```lua
print(exports['meteo-policejob']:IsEscorted()) --> true
```

### GetEscorterId()

The server id of the player escorting them, or `nil`.

```lua
print(exports['meteo-policejob']:GetEscorterId()) --> 14
```

### IsEscorting()

True while this player is escorting someone.

```lua
print(exports['meteo-policejob']:IsEscorting()) --> false
```

### GetEscortedPlayerId()

The server id of the player being escorted, or `nil`.

```lua
print(exports['meteo-policejob']:GetEscortedPlayerId()) --> 22
```

### StopEscorting()

Lets go of the escorted player. Use it before your script puts the escorter in a vehicle, a bed or an animation.

```lua
if exports['meteo-policejob']:IsEscorting() then
    local stopped = exports['meteo-policejob']:StopEscorting()
    print(stopped) --> true
end
```

Returns `false` if they were not escorting anyone, or the server refused (for example a second toggle within 1.5 seconds).

***

## Headbag

### HasHeadbag()

True while the player has a bag over their head.

```lua
if exports['meteo-policejob']:HasHeadbag() then
    return -- they can't see the map
end
```

***

## Shield

### IsShieldActive()

True while the player is holding a riot shield.

```lua
if exports['meteo-policejob']:IsShieldActive() then
    return -- block your emote while the shield is out
end
```
