---
description: Key mash minigame - mash the shown key to fill the disc, used for lockpicking.
---

# Key Mash

A key shows in the middle of a disc and the player mashes it to fill the disc before it drains. Each key in the sequence is one step on the ring, and the player has to clear every step before the timer runs out. It is used for lockpicking, like vehicle keys and pickpocketing.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `keymash`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('keymash', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'medium'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
  * `speedBonus` - percent easier (fewer taps, slower drain and more time). e.g. `20` = 20% easier
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('keymash', 'medium')

if success then
    print('Lock picked!')
else
    print('The pick slipped!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('keymash', {
    keys = { 'E', 'F', 'SPACE' },  -- one step per key
    presses = 8,                   -- taps to fill each step
    drain = 3,                     -- seconds for a full disc to drain
    time = 5,                      -- seconds per step, leave out for no timer
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
