---
description: Reel zone minigame - keep the marker inside the moving zone.
---

# Reel Zone

The player keeps a marker inside a moving zone until the bar fills up. Great for fishing or reeling style actions.

{% hint style="info" %}
The resource name is `meteo-reelzone`.
{% endhint %}

***

## Export

```lua
exports['meteo-reelzone']:startReelZone(difficulty, customOptions)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'` or `'custom'`
* `customOptions` - optional table, only used when difficulty is `'custom'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-reelzone']:startReelZone('medium')

if success then
    print('You reeled it in!')
else
    print('It got away!')
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
