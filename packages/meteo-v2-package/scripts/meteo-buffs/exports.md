---
description: >-
  Every meteo-buffs export with a simple example and what it gives back -
  read and give effects, cravings, stress and hook your own item use.
icon: code
---

# Exports

Read the buffs a player has running, give effects from your own scripts, and work with cravings and stress. Server exports take the player's `source` first. Client exports do not, and always read the local player.

Buff items themselves are built in game with the Buffs creator, not through exports. Use `ItemUsed` (below) when your own script runs the use animation.

***

## Reading Effects

Names you can ask for:

* The built-in modifiers `payout`, `progress`, `lockpick`, `noinjury` and `stressimmune`
* Any tag an owner typed on a Custom effect
* The body numbers `speed`, `stamina`, `damage`, `defense` and `maxhealth`

### HasEffect(source, name) - server

`true` while any running effect gives that modifier.

```lua
if exports['meteo-buffs']:HasEffect(source, 'noinjury') then
    return -- skip the injury
end
```

### GetModifier(source, name) - server

The modifier as a multiplier. `1` when nothing is running.

```lua
local mult = exports['meteo-buffs']:GetModifier(source, 'payout')
print(mult) --> 1.25    (25% payout bonus running)

Player.Functions.AddMoney('cash', math.floor(basePay * mult), 'job-payment')
```

### GetModifierPercent(source, name) - server

The raw percent behind a modifier. `0` when nothing is running.

```lua
local percent = exports['meteo-buffs']:GetModifierPercent(source, 'progress')
print(percent) --> 20

local duration = baseDuration * (1 - percent / 100)
```

### GetActiveEffects(source) - server

One row per running effect, for a status screen. Effects that only move hunger, thirst or stress are left out, since the HUD already shows those bars.

```lua
for _, e in ipairs(exports['meteo-buffs']:GetActiveEffects(source)) do
    print(e.label, e.stat, e.remaining)
end
--> Second wind   +25% stamina   96
```

```lua
-- each row:
{
    id = 'item_meteo_creatine:1',
    label = 'Second wind',    -- the name a player reads
    stat = '+25% stamina',    -- what it does, or nil
    icon = 'ms-sprint',
    color = '#11977f',
    kind = 'buff',            -- 'buff' or 'debuff'
    remaining = 96,           -- seconds left
    duration = 120,           -- seconds in total
    source = 'Creatine',      -- what started it
    announce = false,
}
```

### Client versions

`HasEffect(name)`, `GetModifier(name)`, `GetModifierPercent(name)` and `GetActiveEffects()` work the same on the client, for the local player.

```lua
if exports['meteo-buffs']:HasEffect('lockpick') then
    local bonus = exports['meteo-buffs']:GetModifierPercent('lockpick')
    print(bonus) --> 20
end
```

***

## Giving Effects

### GiveEffects(source, key, effects, cause?, announce?)

Starts effects on a player from your own script.

```lua
local seconds = exports['meteo-buffs']:GiveEffects(source, 'medkit', {
    { effect = 'heal', power = 40 },
    { effect = 'speed', power = -20, duration = 60 },
}, 'Medkit', true)

print(seconds) --> 60    (longest duration started, 0 if nothing started)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `source` | number | Player server id |
| `key` | string | Your own name for this set of effects. Calling again with the same key overwrites what it gave last time instead of stacking |
| `effects` | table | List of effect rows, see below |
| `cause` | string | What the player reads as the reason. Defaults to the key |
| `announce` | boolean | `true` shows the effect names on the HUD as they start. Leave it out for everyday things |

**Effect rows**

```lua
{ effect = 'speed', power = 15, duration = 120 }
```

* `effect` - one of the effect names below. Unknown names are ignored
* `power` - clamped to the effect's own range. Leave it out to use the default
* `duration` - seconds, 5 to 7200, default 120. Ignored by instant effects. A player with the `hu_supplement` perk gets it longer
* `tag` - only for `custom`, the name other scripts read with `HasEffect` and `GetModifier`
* `variant` - only for `screen` (a game postfx name) and `walk` (a walk style)

| Effect | Power | Range |
| ------ | ----- | ----- |
| `speed` | percent | -50 to 45 |
| `stamina` | percent | -75 to 200 |
| `damage` | percent | -50 to 200 |
| `defense` | percent | -50 to 80 |
| `maxhealth` | percent | -25 to 50 |
| `heal` | points, instant | -100 to 200 |
| `hunger` / `thirst` | points per minute | -20 to 20 |
| `stress` | points per minute | -25 to 25 |
| `drunk` | percent | 10 to 100 |
| `shake` | percent | 5 to 150 |
| `ragdoll` | percent | 1 to 100 |
| `payout` | percent | -50 to 200 |
| `progress` | percent | -50 to 75 |
| `lockpick` | percent | -50 to 100 |
| `custom` | percent | -100 to 200 |
| `noinjury` | none | - |
| `stressimmune` | none | - |
| `screen` | none, instant | - |
| `walk` | none | - |

A custom effect your other scripts can read:

```lua
exports['meteo-buffs']:GiveEffects(source, 'gang_turf', {
    { effect = 'custom', power = 10, duration = 600, tag = 'turfbonus' },
}, 'Home turf')

-- somewhere else
local bonus = exports['meteo-buffs']:GetModifierPercent(source, 'turfbonus') --> 10
```

### RemoveEffects(source, key)

Ends everything a key started.

```lua
local removed = exports['meteo-buffs']:RemoveEffects(source, 'medkit')
print(removed) --> true
```

***

## Item Use

### ItemUsed(source, itemName)

For a script that runs its own progress bar for a buff item. Call it when the bar **finishes**, not when the item is used. It applies the item's effects, restores, addiction and cures exactly as if meteo-buffs ran the use itself. It does not remove the item - that is on your script.

```lua
-- after your progress bar completes and you removed the item
local ok = exports['meteo-buffs']:ItemUsed(source, 'meteo_creatine')
print(ok) --> true    (false if the item has no buffs record)
```

***

## Cravings

A craving's key is its name lowercased with spaces turned into underscores, so `Fast food` is `fast_food`. Renaming a craving in the creator changes its key.

### GetCravings(source) - server

Every craving the player has, whether they feel it yet or not. The client version `GetCravings()` returns the same rows for the local player.

```lua
for _, c in ipairs(exports['meteo-buffs']:GetCravings(source)) do
    print(c.label, c.level, c.craving)
end
--> Weed   75   false
```

```lua
-- each row:
{ key = 'weed', label = 'Weed', icon = 'tt-needle', note = nil,
  uses = 3, needs = 4, level = 75, craving = false }
```

### IsCraving(source, key)

`true` while the player is feeling the craving right now.

```lua
print(exports['meteo-buffs']:IsCraving(source, 'weed')) --> false
```

### GetCravingLevel(source, key)

How far into an addiction the player is, 0 to 100.

```lua
print(exports['meteo-buffs']:GetCravingLevel(source, 'weed')) --> 75
```

### CureCraving(source, key, amount)

Takes uses off a craving, the way a detox item does. Returns how many uses were actually removed.

```lua
local removed = exports['meteo-buffs']:CureCraving(source, 'weed', 2)
print(removed) --> 2    (0 if they had none)
```

***

## Stress

### AddStress(source, amount)

Adds stress, or takes it away with a negative amount. Positive amounts are ignored while the player has stress immunity running.

```lua
exports['meteo-buffs']:AddStress(source, 10)
exports['meteo-buffs']:AddStress(source, -15)
```

### GetStress(source)

```lua
print(exports['meteo-buffs']:GetStress(source)) --> 35
```

### SetStress(source, value)

Sets stress to an exact value, clamped to 0 to 100.

```lua
exports['meteo-buffs']:SetStress(source, 0)
```

The old `hud:server:GainStress` and `hud:server:RelieveStress` events from qb-hud still work and route through `AddStress`.

***

## Status Menu

### OpenStatus() - client

Opens the player's character status menu, the same as `/charstatus`.

```lua
exports['meteo-buffs']:OpenStatus()
```

***

## Statebags

Everything above is also on the player's statebag, so you can watch it without calling an export.

```lua
-- server
Player(source).state.buffs      -- the effect rows
Player(source).state.buffMods   -- the folded numbers, flags and tags
Player(source).state.cravings   -- the craving rows

-- client, local player
LocalPlayer.state.buffMods.tags.payout
```

`buffMods` holds `speed`, `stamina`, `damage`, `defense`, `maxhealth`, `shake`, `ragdoll`, `drunk`, `screen`, `walk`, a `tags` map and a `drains` map. Every number is a percent except `drains`, which is per minute.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
