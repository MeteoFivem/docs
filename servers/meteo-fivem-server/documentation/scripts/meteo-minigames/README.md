---
description: >-
  Standalone minigames included with the meteo fivem server. Each one is a single
  export you call from any script and it returns true on success.
---

# Meteo Minigames

A set of standalone minigames you can drop into any script. Every minigame is its own resource and exposes one export. You call the export, the player plays the minigame, and you get back `true` (passed) or `false` (failed or cancelled).

{% hint style="info" %}
All minigames follow the same pattern. The call blocks until the player finishes, so you can use the result right away with a simple `if`.
{% endhint %}

***

## How They Work

```lua
local success = exports['resource-name']:exportName('medium')

if success then
    -- player passed
else
    -- player failed or closed the minigame
end
```

* `difficulty` is usually `'easy'`, `'medium'` or `'hard'` (some have `'extreme'` or `'custom'`).
* The export returns a boolean, so there is no need for callbacks or events.

{% hint style="warning" %}
Call minigame exports from the **client** side only.
{% endhint %}

***

## Available Minigames

* [Arrow Timing](meteo-arrowtiming.md) - hit arrows in time as they cross the timing zone
* [E-Timing](meteo-etiming.md) - stop the moving bar inside the target boxes
* [Lockpick](meteo-lockopen.md) - rotating circle lockpick
* [Circle Pick](meteo-circlepick.md) - click circles before they disappear
* [Fuse Box](meteo-fuseboxfix.md) - repeat the fuse sequence each round
* [Gym Training](meteo-gymtrain.md) - rhythm based training minigame
* [Reel Zone](meteo-reelzone.md) - keep the marker inside the moving zone

***

{% hint style="success" %}
**Need help integrating these?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
