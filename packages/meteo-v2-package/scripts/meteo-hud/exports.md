---
description: >-
  Every meteo-hud export with a simple example - custom statuses, buffs,
  vehicle indicators, XP pills, cruise control, the speed limiter and hiding the
  HUD.
icon: code
---

# Exports

Add your own statuses, buffs and vehicle indicators to the HUD, show XP gains, and drive cruise control or the HUD's visibility from your own scripts.

Client exports act on the calling player. Most of them also have a server version that takes the player's server id first - see [Server](#server) at the bottom.

**Icons** - statuses, buffs and indicators take any <a href="https://lucide.dev/icons" target="_blank">Lucide</a> icon name in kebab-case (`pill`, `radiation`, `flame`). An unknown name shows a circle.

***

## Client: Statuses

Statuses are 0-100 values shown as chips next to the vitals, like hunger and thirst. `hunger`, `thirst`, `stress`, `stamina` and `oxygen` are built in.

### RegisterStatus(id, def)

Adds a status, or updates its look if the id already exists.

```lua
exports['meteo-hud']:RegisterStatus('radiation', {
    icon      = 'radiation',
    color     = '#F5D90A',
    order     = 50,     -- lower sits first
    showAbove = 0,      -- hidden until the value goes past 0
    lowAbove  = 75,     -- turns red past 75
    value     = 0,
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `icon` | string | Defaults to `circle` |
| `color` | string | Hex. Defaults to `#F5F9FC` |
| `order` | number | Defaults to 50 |
| `showBelow` / `showAbove` | number | The chip stays hidden until the value crosses this. Leave out to always show |
| `lowBelow` / `lowAbove` | number | The chip turns red past this |
| `value` | number | Starting value, 0-100 |
| `label` | string | Text or a locale key shown on an announce card |
| `announce` | string | `'show'` pops the card when the chip appears, `'high'` when it turns red |

### SetStatus(id, value, labelArg?)

```lua
exports['meteo-hud']:SetStatus('radiation', 42)
exports['meteo-hud']:SetStatus('hunger', 80)
```

`value` is clamped to 0-100. `labelArg` fills a `%s` in the status label. Does nothing for an id that was never registered.

### GetStatus(id)

```lua
print(exports['meteo-hud']:GetStatus('thirst')) --> 64
--> nil for an unknown id
```

### RemoveStatus(id)

```lua
exports['meteo-hud']:RemoveStatus('radiation')
```

***

## Client: Buffs

Timed chips in the effects row above the vitals, like painkillers or a food bonus. A new buff id announces its name first.

### SetBuff(id, def)

Adds or replaces a buff. Passing `nil` as `def` clears it.

```lua
exports['meteo-hud']:SetBuff('painkillers', {
    label     = 'Painkillers',
    icon      = 'pill',
    color     = '#57EFAF',
    kind      = 'buff',   -- 'buff' or 'debuff'
    remaining = 120,      -- seconds left
    duration  = 300,      -- total seconds, draws the ring
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `label` | string | Defaults to the id |
| `icon` | string | Defaults to `sparkles` |
| `color` | string | Defaults to `#57EFAF` |
| `kind` | string | `buff` or `debuff` |
| `order` | number | Defaults to 50 |
| `stacks` | number | Stack count, defaults to 1 |
| `quiet` | boolean | Skips the name announcement. Good for everyday food |
| `remaining` + `duration` | number | Seconds. Use these for a timer |
| `progress` | number | 0-1. Use this instead of a timer for anything without a clock |

### ClearBuff(id)

```lua
exports['meteo-hud']:ClearBuff('painkillers')
```

***

## Client: Vehicle Indicators

Tiles in the vehicle dock under the built-in ones (lights, seatbelt, cruise, engine, lock).

### RegisterIndicator(id, def)

```lua
exports['meteo-hud']:RegisterIndicator('harness', {
    icon  = 'shield',
    label = 'Harness',
    color = '#57EFAF',             -- tile colour when on
    order = 25,
    kinds = { car = true },        -- leave out to show on every vehicle type
    state = 'on',
})
```

`state` is `'off'` (hidden), `'on'`, `'warn'` (amber) or `'alert'` (red and blinking). `true` and `false` work as `'on'` and `'off'`. `alertIcon` swaps the icon while in `alert`.

### SetIndicator(id, state) / GetIndicator(id)

```lua
exports['meteo-hud']:SetIndicator('harness', 'warn')
print(exports['meteo-hud']:GetIndicator('harness')) --> warn
```

### RemoveIndicator(id)

```lua
exports['meteo-hud']:RemoveIndicator('harness')
```

### SetVehicleAux(def)

The small arc on the left of the speedometer, for things like nitrous. Pass `nil` to remove it.

```lua
exports['meteo-hud']:SetVehicleAux({
    label  = 'NOS',
    value  = 0.6,       -- 0-1
    color  = '#1596c9',
    active = true,      -- in use right now
})

exports['meteo-hud']:SetVehicleAux(nil)
```

***

## Client: Driving

### SetSeatbelt(state) / GetSeatbelt()

Tells the HUD whether the seatbelt is on. Call it from your seatbelt script.

```lua
exports['meteo-hud']:SetSeatbelt(true)
print(exports['meteo-hud']:GetSeatbelt()) --> true
```

### SetCruise(value) / GetCruise()

`true` holds the current speed, a number holds that speed in the player's unit (`Config.speedUnit`), `false` turns it off.

```lua
local ok = exports['meteo-hud']:SetCruise(60)
print(ok) --> true
--> false if not the driver, cruise is off in config, or the vehicle is not moving forward

print(exports['meteo-hud']:GetCruise()) --> 60   (false when off)
```

### SetSpeedLimit(value) / GetSpeedLimit()

Same arguments as `SetCruise`, for the speed limiter.

```lua
exports['meteo-hud']:SetSpeedLimit(80)
print(exports['meteo-hud']:GetSpeedLimit()) --> 80
```

***

## Client: Medical

For an ambulance or medical script.

### SetBleeding(state)

```lua
exports['meteo-hud']:SetBleeding(true)
```

### SetHealing(target)

The health percent the current treatment heals up to. Pass `false` when it ends. Ignored while dead.

```lua
exports['meteo-hud']:SetHealing(75)
exports['meteo-hud']:SetHealing(false)
```

### SetReviving(value)

Revive progress while downed. A number from 0 to 1, `true` for a revive with no timer, `false` when done.

```lua
exports['meteo-hud']:SetReviving(0.4)
```

***

## Client: XP and Visibility

### ShowXp(def)

A short pill under the compass. Sending the same `key` again while it is on screen updates it.

```lua
exports['meteo-hud']:ShowXp({
    key      = 'lockpicking',
    label    = 'Lockpicking',
    icon     = 'key',           -- a Material Symbols name
    color    = '#ff5d52',
    gained   = 25,
    into     = 85,              -- XP into the current level
    needed   = 150,             -- XP the level needs
    level    = 4,
    levelled = false,           -- true plays the level up version
    duration = 4000,            -- ms, 1500-15000
})
```

`label` is required.

### SetHidden(reason, state) / IsHidden(reason?)

Hides the whole HUD while any reason is set, so two scripts hiding it at once do not undo each other. A reason is cleared on its own if your resource stops.

```lua
exports['meteo-hud']:SetHidden('cutscene', true)
-- later
exports['meteo-hud']:SetHidden('cutscene', false)

print(exports['meteo-hud']:IsHidden('cutscene')) --> false
print(exports['meteo-hud']:IsHidden())           --> true when the HUD is hidden for any reason
```

***

## Server

The same exports from the server, with the player's server id first. They send the call to that player's client.

```lua
exports['meteo-hud']:SetBuff(source, 'painkillers', { label = 'Painkillers', icon = 'pill', remaining = 120, duration = 300 })
exports['meteo-hud']:ClearBuff(source, 'painkillers')
exports['meteo-hud']:RegisterStatus(source, 'radiation', { icon = 'radiation', color = '#F5D90A', showAbove = 0 })
exports['meteo-hud']:SetStatus(source, 'radiation', 42)
exports['meteo-hud']:SetHidden(source, 'cutscene', true)
```

Available: `RegisterStatus`, `SetStatus`, `RemoveStatus`, `SetBuff`, `ClearBuff`, `RegisterIndicator`, `SetIndicator`, `RemoveIndicator`, `SetVehicleAux`, `SetSeatbelt`, `SetCruise`, `SetSpeedLimit`, `SetBleeding`, `SetHealing`, `SetReviving`, `SetHidden`.

Each returns `true` once sent, or `false` for an invalid source. Getters are client only.

***

## Compatibility

Scripts still sending the old HUD events keep working:

* `hud:client:UpdateNeeds(hunger, thirst)` and `hud:client:UpdateStress(stress)`
* `seatbelt:client:ToggleSeatbelt(state?)` and `seatbelt:client:ToggleCruise(state?)`
* `hud:client:UpdateHarness(hp)` and `hud:client:UpdateNitrous(level, hasNitro)`
* `hud:client:UpdateDrunk(value)`, `hud:client:UpdateAddiction(value, substance?)`, `hud:client:UpdateFoodAddiction(category, level)`

New scripts should use the exports above.
