---
description: Lockpick minigame - stop the rotating marker on the right spot.
icon: lock-open
---

# Lockpick

A rotating circle lockpick. The player stops the marker inside the target area, harder difficulties add more circles.

{% hint style="info" %}
The resource name is `meteo-lockopen`.
{% endhint %}

***

## Export

```lua
exports['meteo-lockopen']:startLockpick(difficulty)
```

* `difficulty` - `'easy'`, `'medium'` or `'hard'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-lockopen']:startLockpick('easy')

if success then
    print('Lock opened!')
else
    print('The lock jammed!')
end
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
