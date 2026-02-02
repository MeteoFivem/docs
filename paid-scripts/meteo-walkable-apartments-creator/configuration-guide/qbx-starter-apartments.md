# QBX Starter Apartments

Use Meteo Apartments as the starter apartment system for QBX. New players choose an apartment when they create their character.

***

## How it works

When a new character is created:

1. QBX calls the Meteo Apartments spawn selection export
2. Player sees a menu with available starter apartments
3. Player chooses an apartment or default spawn
4. Apartment is created FREE (no money charged)
5. Player spawns inside their new apartment

{% hint style="info" %}
**Compatibility:** Works with QBX qbx_core default character system. For custom multicharacter systems, contact support.
{% endhint %}

***

## Setup Instructions

{% stepper %}
{% step %}
### Enable Starter Apartments

Open `meteo-apartments/shared/config.lua` and enable starter apartments:

```lua
Config.starterApartments = {
    enabled = true,
    defaultSpawn = vec4(-1038.46, -2738.15, 13.76, 324.22), -- Change to your spawn
}
```

Change `defaultSpawn` to your server's default spawn point. This is used if the player chooses "Default Spawn" instead of an apartment.


{% endstep %}

{% step %}
### Update qbx_core

Open `qbx_core/client/character.lua` and find lines 348-350:

**Find this code:**

```lua
if config.characters.startingApartment then
    TriggerEvent('apartments:client:setupSpawnUI', newData)
else
    TriggerEvent('qbx_core:client:spawnNoApartments')
end
```

**Replace with this:**

```lua
if config.characters.startingApartment then
    local success = exports['meteo-apartments']:OpenSpawnSelection()
    if not success then
        TriggerEvent('qbx_core:client:spawnNoApartments')
    end
else
    TriggerEvent('qbx_core:client:spawnNoApartments')
end
```

{% hint style="success" %}
**Only ONE line changes.** Line 349 is the only change needed in qbx_core.
{% endhint %}


{% endstep %}

{% step %}
### Comment Out qbx_properties Listener

Open `qbx_properties/server/apartmentselect.lua` and comment out the `QBCore:Server:OnPlayerLoaded` event (around line 71-78):

```lua
-- RegisterNetEvent('QBCore:Server:OnPlayerLoaded', function()
--     local playerSource = source
--     local player = exports.qbx_core:GetPlayer(playerSource)
--     local hasApartment = MySQL.single.await('SELECT * FROM properties WHERE owner = ?', {player.PlayerData.citizenid})
--     if not hasApartment then
--         TriggerClientEvent('apartments:client:setupSpawnUI', playerSource)
--     end
-- end)
```

This prevents qbx_properties from interfering with the spawn selection.


{% endstep %}

{% step %}
### Enable Complexes for Starter Apartments

Mark which apartment complexes can be used as starter apartments.

Open your complex config file (e.g., `shared/complexes/wiwang_hotel.lua`) and add `startingEnabled = true`:

```lua
return {
    label = 'WiWang Hotel',
    coords = vec3(-824.73, -702.12, 28.06),
    startingEnabled = true,  -- Enable for spawn selection
    totalRooms = 20,
    roomType = 'modern',
    -- ...
}
```

Only complexes with `startingEnabled = true` will appear in the spawn selection menu.


{% endstep %}

{% step %}
### Test It

1. Restart your server
2. Create a new character
3. You should see the apartment selection menu
4. Choose an apartment or default spawn
5. Player spawns in the selected location

{% hint style="warning" %}
**First spawn triggers clothing selection.** If you have a clothing script (illenium-appearance, qb-clothing), it will open automatically on first spawn.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## Configuration Options

### Default Spawn Point

The spawn point used when player chooses "Default Spawn":

```lua
Config.starterApartments = {
    defaultSpawn = vec4(-1038.46, -2738.15, 13.76, 324.22),
}
```

Change this to your server's spawn point.

### Enable/Disable Per Complex

Control which complexes appear in spawn selection:

```lua
-- In complex config file
return {
    startingEnabled = true,  -- Shows in spawn selection
    -- or
    startingEnabled = false, -- Hidden from spawn selection
}
```

***

## How It Works Technically

### Export-Based Integration

Uses secure export instead of events:

```lua
exports['meteo-apartments']:OpenSpawnSelection()
```

This is safer than event-based systems and prevents exploits.

### Apartment Creation

When a player chooses an apartment:

1. System checks if player already has an apartment (anti-cheat)
2. Validates the complex is a valid starter complex
3. Finds first available room in the complex
4. Creates apartment FREE (no money charged)
5. Spawns player inside using `spawnInsideApartment()` export

### First Spawn Handling

The `isFirstTime = true` parameter triggers:
- Clothing selection (if you have clothing script)
- First-time setup (if needed by other scripts)

***

## Anti-Cheat Features

### Already Has Apartment Check

System checks if player already owns an apartment before creating a new one. Prevents exploit attempts.

### Valid Complex Validation

Only complexes with `startingEnabled = true` can be used. Prevents invalid complex IDs.

### No Apartment Ownership Check

Unlike qbx_properties, we don't check for existing property ownership. This keeps it simple and prevents conflicts with other property systems.

***

## Troubleshooting

### Menu not showing?

Check that `Config.starterApartments.enabled = true` in config.lua.

### No complexes in menu?

Make sure at least one complex has `startingEnabled = true` in its config.

### Player spawns at default spawn?

Check that the complex has available rooms. If all rooms are taken, player spawns at default spawn.

{% hint style="danger" %}
**Important:** Make sure you commented out the qbx_properties listener. Having both systems active will cause conflicts.
{% endhint %}

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
