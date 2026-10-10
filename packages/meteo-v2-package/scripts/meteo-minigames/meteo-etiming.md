---
description: E-Timing minigame - press E as the needle passes each point on the track.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-etiming.md
---

# E-Timing

A needle moves along a track and the player presses E each time it passes one of the highlighted points.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `etiming`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('etiming', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'easy'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('etiming', 'hard')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('etiming', {
    duration = 2000,   -- ms for one pass of the needle
    minBoxCount = 3,   -- fewest points on the track
    maxBoxCount = 6,   -- most points on the track
    tolerance = 25,    -- hit window
    maxFails = 1,      -- fails before losing
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
