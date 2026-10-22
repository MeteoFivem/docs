---
description: >-
  Every meteo-animations export with a simple example - play and cancel emotes,
  walk styles, hands up and pointing checks.
icon: code
---

# Exports

Play emotes and read the player's animation state from your own scripts. Every export is client side and acts on the calling player.

***

## Emotes

### EmoteCommandStart(emoteName, textureVariation?)

Plays an emote, same as typing `/e <name>`. Works for emotes, dances, prop emotes, animal emotes and expressions.

```lua
exports['meteo-animations']:EmoteCommandStart('notepad')
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `emoteName` | string | The `/e` name, not case sensitive. `'c'` cancels the current emote |
| `textureVariation` | number | Optional, starts at 1. Only used by a custom prop emote that has `PropTextureVariations` in its `AnimationOptions` - none of the shipped emotes do |

Returns nothing. Dead players, players swimming (unless `Config.allowInWater`) and unknown names get a notification instead.

### EmoteCancel(force?)

Stops the current emote and removes its props. Also drops hands up.

```lua
exports['meteo-animations']:EmoteCancel()
exports['meteo-animations']:EmoteCancel(true) -- ignores CanCancelEmote(false)
```

### CanCancelEmote(state)

Locks the emote so the player cannot cancel it with the cancel key or `/e c`. Useful while your script is running a timed task.

```lua
exports['meteo-animations']:EmoteCommandStart('mechanic')
exports['meteo-animations']:CanCancelEmote(false)

Wait(10000)

exports['meteo-animations']:CanCancelEmote(true)
exports['meteo-animations']:EmoteCancel()
```

Always set it back to `true` when you are done.

### IsPlayerInAnim()

The name of the emote playing, or `nil`.

```lua
local emote = exports['meteo-animations']:IsPlayerInAnim()
print(emote) --> sitchair
```

The same value is on `LocalPlayer.state.currentEmote`.

### getCurrentEmote()

The name of the last emote started, or `nil` once it is cancelled.

```lua
print(exports['meteo-animations']:getCurrentEmote()) --> notepad
```

### IsPlayerPointing()

```lua
if exports['meteo-animations']:IsPlayerPointing() then
    -- finger is out
end
```

***

## Walk Styles

### setWalkstyle(clipset, force?)

Sets a walk style by its clipset name. Pass `nil` or `''` to reset to the default walk. Saved per character when `Config.persistentWalk` is on.

```lua
exports['meteo-animations']:setWalkstyle('move_m@drunk@verydrunk')
exports['meteo-animations']:setWalkstyle(nil) -- reset
```

### getWalkstyle()

The current clipset name, or `nil` for the default walk.

```lua
print(exports['meteo-animations']:getWalkstyle()) --> move_m@drunk@verydrunk
```

### toggleWalkstyle(bool, message)

Does nothing. Only there so scripts that call it do not error.

***

## Hands Up

### getHandsup()

```lua
if exports['meteo-animations']:getHandsup() then
    -- player has their hands up
end
```

### cancelHandsup()

Puts the player's hands down.

```lua
exports['meteo-animations']:cancelHandsup()
```

***

## Compatibility

`getHandsup` and `cancelHandsup` also answer `exports['qb-smallresources']:...`, so scripts written for qb-smallresources hands up keep working without changes.
