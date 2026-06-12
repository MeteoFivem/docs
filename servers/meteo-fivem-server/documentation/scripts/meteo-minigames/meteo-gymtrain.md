---
description: Gym training minigame - hit the keys in rhythm to complete the set.
---

# Gym Training

A rhythm based training minigame. The player hits the keys in time to finish the set.

{% hint style="info" %}
The resource name is `meteo-gymtrain`.
{% endhint %}

***

## Export

```lua
exports['meteo-gymtrain']:startGymTraining(difficulty, customOptions)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'`, `'extreme'` or `'custom'`
* `customOptions` - optional table, only used when difficulty is `'custom'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-gymtrain']:startGymTraining('medium')

if success then
    print('Set complete!')
else
    print('You gave up!')
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
