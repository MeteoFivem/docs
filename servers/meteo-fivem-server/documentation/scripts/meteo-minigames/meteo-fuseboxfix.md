---
description: Fuse box minigame - repeat the fuse sequence each round.
icon: plug-circle-bolt
---

# Fuse Box

The player has to repeat a fuse sequence each round before the timer runs out.

{% hint style="info" %}
The resource name is `meteo-fuseboxfix`.
{% endhint %}

***

## Export

```lua
exports['meteo-fuseboxfix']:startFuseBox(difficulty, customOptions)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'`, `'extreme'` or `'custom'`
* `customOptions` - optional table, only used when difficulty is `'custom'`
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-fuseboxfix']:startFuseBox('medium')

if success then
    print('Power restored!')
else
    print('You blew a fuse!')
end
```

### Custom Options

```lua
local success = exports['meteo-fuseboxfix']:startFuseBox('custom', {
    fusesPerRound = 5,        -- fuses to match each round
    totalRounds = 3,          -- number of rounds
    maxFailedAttempts = 2,    -- fails before losing
    timeLimit = 4000,         -- ms per round
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
