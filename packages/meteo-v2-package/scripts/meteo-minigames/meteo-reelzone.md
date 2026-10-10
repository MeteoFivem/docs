---
description: Reel zone minigame - keep the fish inside the catch zone until the bar fills.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-reelzone.md
---

# Reel Zone

The player holds SPACE to keep the fish inside the moving catch zone until the progress bar fills up. Great for fishing or reeling style actions.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `reelzone`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('reelzone', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'medium'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('reelzone', 'medium')

if success then
    print('You reeled it in!')
else
    print('It got away!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('reelzone', {
    zoneSize = 0.30,       -- catch zone size (0-1)
    fishSpeed = 0.5,       -- how fast the fish moves
    progressRate = 0.18,   -- bar fill speed while caught
    drainRate = 0.07,      -- bar drain speed while lost
    dartChance = 0.008,    -- chance the fish darts
    dartSpeed = 1.8,       -- dart speed
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
