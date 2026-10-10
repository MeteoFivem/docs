---
description: Circle pick minigame - click the numbered circles in rhythm.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-circlepick.md
---

# Circle Pick

Numbered circles pop up on screen and the player has to click them in rhythm before they vanish.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `circlepick`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('circlepick', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'` (default `'medium'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
  * `speedBonus` - percent more time between circles (higher = easier). e.g. `42` = 42% more time
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('circlepick', 'medium')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('circlepick', {
    targetCount = { 10, 12 },  -- {min, max} circles, randomized
    interval = { 300, 340 },   -- {min, max} ms between circles, randomized
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
