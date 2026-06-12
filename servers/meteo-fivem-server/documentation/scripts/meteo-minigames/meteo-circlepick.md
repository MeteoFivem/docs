---
description: Circle pick minigame - click the circles before they disappear.
---

# Circle Pick

Circles pop up on screen and the player has to click them before they vanish.

{% hint style="info" %}
The resource name is `meteo-circlepick`. Note its export is also called `startLockpick`.
{% endhint %}

***

## Export

```lua
exports['meteo-circlepick']:startLockpick(difficulty, timeLimit, speedBonus)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'`
* `timeLimit` - optional, overall time limit
* `speedBonus` - optional, percent to slow the circles down (higher = easier). e.g. `42` = 42% more time
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-circlepick']:startLockpick('medium')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

### With Speed Bonus

```lua
-- give the player 42% more time per circle
local success = exports['meteo-circlepick']:startLockpick('hard', nil, 42)
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
