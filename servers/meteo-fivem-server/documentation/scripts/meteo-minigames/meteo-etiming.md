---
description: E-Timing minigame - stop the moving bar inside the target boxes.
icon: gauge-high
---

# E-Timing

A bar moves across a track and the player presses to stop it inside the highlighted target boxes.

***

## Export

```lua
exports['meteo-etiming']:startETiming(difficulty)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-etiming']:startETiming('hard')

if success then
    print('You did it!')
else
    print('You failed!')
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
