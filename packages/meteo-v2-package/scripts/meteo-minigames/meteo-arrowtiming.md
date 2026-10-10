---
description: Arrow timing minigame - press the shown arrow key before the timer runs out.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-arrowtiming.md
---

# Arrow Timing

An arrow shows on screen and the player has to press the matching arrow key before the timer runs out.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `arrowtiming`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('arrowtiming', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'easy'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('arrowtiming', 'medium')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('arrowtiming', {
    arrows = 4,            -- arrows per cycle
    cycles = 3,            -- number of cycles
    timePerArrow = 700,    -- ms allowed per arrow
    maxFails = 1,          -- fails before losing
    randomArrows = true,   -- randomize arrow directions
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
