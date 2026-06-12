---
description: Arrow timing minigame - hit arrows as they cross the timing zone.
icon: arrows-up-down
---

# Arrow Timing

Arrows scroll across the screen and the player has to hit each one as it lines up with the timing zone.

***

## Export

```lua
exports['meteo-arrowtiming']:startArrowTiming(difficulty, customOptions)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'` or `'custom'`
* `customOptions` - optional table, only used when difficulty is `'custom'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-arrowtiming']:startArrowTiming('medium')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

### Custom Options

```lua
local success = exports['meteo-arrowtiming']:startArrowTiming('custom', {
    arrows = 4,            -- arrows per cycle
    cycles = 3,            -- number of cycles
    timePerArrow = 700,    -- ms allowed per arrow
    maxFails = 1,          -- fails before losing
    randomArrows = true,   -- randomize arrow directions
    allowMovement = false, -- let the player still move while playing
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
