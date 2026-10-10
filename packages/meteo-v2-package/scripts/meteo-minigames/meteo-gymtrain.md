---
description: Gym training minigame - press E while the moving cursor is inside the zone.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-gymtrain.md
---

# Gym Training

A cursor moves along a bar and the player presses E while it is inside the zone, once per rep. The cursor speeds up and the zone shrinks as the set goes on.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `gymtrain`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('gymtrain', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'` or `'extreme'` (default `'medium'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('gymtrain', 'medium')

if success then
    print('Set complete!')
else
    print('You gave up!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('gymtrain', {
    reps = 8,               -- reps to finish the set
    speed = 1.4,            -- cursor speed
    zoneSize = 0.22,        -- zone width (0-1)
    maxMisses = 2,          -- misses before losing
    speedIncrease = 0.08,   -- extra speed per rep
    zoneShrink = 0.012,     -- zone shrink per rep
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
