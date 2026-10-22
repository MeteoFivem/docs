---
description: >-
  All Meteo V2 minigames in one resource, meteo-minigames. One export starts
  any minigame and returns true on success.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-minigames/
---

# Meteo Minigames

Every Meteo minigame now lives in one resource: `meteo-minigames`. You call one export with the name of the minigame you want, the player plays it, and you get back `true` (passed) or `false` (failed or cancelled).

{% hint style="info" %}
The old standalone resources (`meteo-arrowtiming`, `meteo-etiming`, `meteo-lockopen`, `meteo-circlepick`, `meteo-fuseboxfix`, `meteo-gymtrain`, `meteo-reelzone`) are merged into `meteo-minigames`. If you used their old exports, switch them to `exports['meteo-minigames']:Start(...)`.
{% endhint %}

***

## How They Work

```lua
local success = exports['meteo-minigames']:Start(game, difficulty, options)

if success then
    -- player passed
else
    -- player failed or closed the minigame
end
```

* `game` - `'arrowtiming'`, `'circlepick'`, `'etiming'`, `'fusebox'`, `'gymtrain'`, `'keymash'`, `'lockopen'` or `'reelzone'`
* `difficulty` - optional, a preset name like `'easy'`, `'medium'` or `'hard'` (some have `'extreme'`), or your own settings table. A custom table is merged over the minigame's default preset, so you only pass what you want to change.
* `options` - optional table:
  * `speedBonus` - percent easier (used by circlepick and keymash)
  * `allowMovement` - the player can keep moving while playing
* **Returns** `true` if passed, `false` if failed, cancelled with Escape, or if another minigame is already running

The call blocks until the player finishes, so you can use the result right away with a simple `if`.

### Other Exports

```lua
exports['meteo-minigames']:Cancel()   -- close the running minigame as a fail (e.g. the player died)
exports['meteo-minigames']:IsActive() -- true while a minigame is open
```

{% hint style="warning" %}
Call minigame exports from the **client** side only.
{% endhint %}

***

## Available Minigames

* [Arrow Timing](meteo-arrowtiming.md) - press the shown arrow key before the timer runs out
* [E-Timing](meteo-etiming.md) - press E as the needle passes each point on the track
* [Lockpick](meteo-lockopen.md) - press E as the dot passes each pin on the circle
* [Circle Pick](meteo-circlepick.md) - click the numbered circles in rhythm
* [Fuse Box](meteo-fuseboxfix.md) - click the broken fuses before time runs out
* [Gym Training](meteo-gymtrain.md) - stop the moving cursor inside the zone, once per rep
* [Reel Zone](meteo-reelzone.md) - keep the fish inside the catch zone until the bar fills
* [Key Mash](meteo-keymash.md) - mash the shown key to fill the disc, used for lockpicking

***

## Test Command

{% hint style="warning" %}
This is a testing command and only works on our showcase server.
{% endhint %}

```
/minigame <game> [difficulty]
```

Starts any minigame with the given preset, for example `/minigame keymash hard`.

***

All difficulty presets are configurable on our config. You can change them once you get the package. We will guide you :)

{% hint style="success" %}
**Need help integrating these?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
