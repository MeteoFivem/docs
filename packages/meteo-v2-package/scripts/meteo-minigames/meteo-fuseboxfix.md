---
description: Fuse box minigame - click the broken fuses before time runs out.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/meteo-fuseboxfix.md
---

# Fuse Box

The player has to find and click the broken fuses each round before the timer runs out.

{% hint style="info" %}
This minigame is part of `meteo-minigames`. The game name is `fusebox`.
{% endhint %}

***

## Export

```lua
exports['meteo-minigames']:Start('fusebox', difficulty, options)
```

* `difficulty` - `'easy'`, `'medium'`, `'hard'` or `'extreme'` (default `'medium'`), or a custom settings table (see below)
* `options` - optional, see the [Meteo Minigames](README.md) page
* **Returns** `true` if passed, `false` if failed or closed

***

## Example

```lua
local success = exports['meteo-minigames']:Start('fusebox', 'medium')

if success then
    print('Power restored!')
else
    print('You blew a fuse!')
end
```

### Custom Settings

Pass a table instead of a preset name. It is merged over the default preset, so you only need the values you want to change.

```lua
local success = exports['meteo-minigames']:Start('fusebox', {
    fusesPerRound = 5,        -- fuses to fix each round
    totalRounds = 3,          -- number of rounds
    maxFailedAttempts = 2,    -- fails before losing
    timeLimit = 4000,         -- ms per round
})
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
