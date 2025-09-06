---
icon: joystick
---

# Circle pick minigame

{% hint style="info" %}
Purchase This Script from: [Meteo Circlepick Minigame](https://meteofivem.net/fivem-scripts/prodigy-rp-inspired-circlepick-minigame)
{% endhint %}

## Installation Guide

#### QBCore Framework (qb-vehiclekeys)

**Pre-configured Version (Recommended)** You can just download qb-vehiclekeys modified for support of meteo-circlepick - [https://github.com/MeteoFivem/qb-vehiclekeys](https://github.com/MeteoFivem/qb-vehiclekeys)

**Manual**

* Go to `[qb]/qb-vehiclekeys/client/main.lua`
* Look for `RegisterNetEvent('lockpicks:UseLockpick')` event
* Find `local success = exports['qb-minigames']:Skillbar(difficulty)`
* Replace it with `local success = exports['meteo-circlepick']:startLockpick(difficulty, nil)`

#### QBox Framework (qbx\_vehiclekeys)

**Pre-configured Version (Recommended)** You can just download qbx\_vehiclekeys modified for support of meteo-circlepick - [https://github.com/MeteoFivem/qbx\_vehiclekeys](https://github.com/MeteoFivem/qbx_vehiclekeys)

**Manual**

* Go to `[qbx]/qbx_vehiclekeys/client/functions.lua`
* Look for function `LockpickDoor`
* Find `local isSuccess = customChallenge or lib.skillCheck(skillCheckConfig.difficulty, skillCheckConfig.inputs)`
* Replace it with `local isSuccess = customChallenge or exports['meteo-circlepick']:startLockpick(difficulty, nil)`
* Again look for function `Hotwire`
* Find the skillCheck line
* Replace it with `local isSuccess = customChallenge or exports['meteo-circlepick']:startLockpick(skillCheckConfig.difficulty, nil)`

### For Developers

Export the lockpick function in your scripts:

```lua
local success = exports['meteo-circlepick']:startLockpick(difficulty, timeLimit)
```

#### Parameters

* `difficulty`: String - "easy", "medium", or "hard"
* `timeLimit`: Number - Time limit in seconds

#### Event Handler

```lua
TriggerEvent('meteo-circlepick:client:openLockpick', function(success)
    if success then
        -- Handle successful lockpick
    else
        -- Handle failed lockpick
    end
end)
```

### Note

This script is exclusively available through official Meteo FiveM Studios and we are only selling this script through Tebex and it comes to your FiveM CFX Account. Beware of unauthorized copies or scams from other sources.

_For technical support, bug reports, or questions, please use our Discord server. We're here to help!_
