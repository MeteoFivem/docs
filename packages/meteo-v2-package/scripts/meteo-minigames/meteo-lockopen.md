---
description: Lockpick minigame - press E as the dot passes each pin on the circle.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-lockopen.md
---

# Lockpick

A rotating circle lockpick. The player presses E as the dot passes each pin on the circle, harder difficulties add more pins and spin faster.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `lockopen`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('lockopen', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'easy'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('lockopen', 'easy')

if success then
    print('Lock opened!')
else
    print('The lock jammed!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('lockopen', {
    numCircles = 5,     -- pins to hit
    speed = 2200,       -- ms per lap
    hitTolerance = 24,  -- hit window
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
