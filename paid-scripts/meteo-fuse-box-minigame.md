# Meteo Fuse box minigame

{% hint style="info" %}
Purchase This Script from: [Meteo Fuse box minigame](https://meteo.tebex.io/package/7195757)
{% endhint %}

### Installation

1. Create a folder named `meteo-fuseboxfix` in your `resources` directory
2. Place all files in the folder
3. Add to your `server.cfg`:

```
ensure meteo-fuseboxfix
```

4. Restart your server

### For Developers

Export the minigame in your scripts:

```lua
local success = exports['meteo-fuseboxfix']:startFuseBox(difficulty, customConfig)
```

#### Parameters

* `difficulty`: String - "easy", "medium", "hard", or "custom"
* `customConfig`: Table (optional) - Custom configuration for the minigame

#### Custom Configuration Example

```lua
local success = exports['meteo-fuseboxfix']:startFuseBox('custom', {
    fusesPerRound = 5,
    totalRounds = 3,
    maxFailedAttempts = 2,
    timeLimit = 4000
})
```

#### Integration Examples

```lua
RegisterCommand('lockpick', function()
    local success = exports['meteo-fuseboxfix']:startFuseBox('medium')
    
    if success then
        -- Handle successful lockpick
    else
        -- Handle failed lockpick
    end
end)
```

```lua
-- Simple usage with default medium difficulty
local success = exports['meteo-fuseboxfix']:startFuseBox('medium')

if success then
    print('Player succeeded!')
    -- Give rewards, unlock door, etc.
else
    print('Player failed!')
    -- Handle failure
end
```

### Note

This script is exclusively available through official Meteo Studios FiveM and we are only selling this script through Tebex and it comes to your FiveM CFX Account. Beware of unauthorized copies or scams from other sources.

_For technical support, bug reports, or questions, please use our Discord server. We're here to help!_
