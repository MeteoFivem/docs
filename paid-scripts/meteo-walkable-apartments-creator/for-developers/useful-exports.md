# Useful Exports

## Quick Exports Reference Table

| Export                                                   | Purpose                                       | Side             |
| -------------------------------------------------------- | --------------------------------------------- | ---------------- |
| `exports['meteo-apartments']:getCurrentApartment`        | Get current apartment player is in            | Client side Only |
| `exports['meteo-apartments']:isInsideApartment`          | Check if player is inside apartment           | Client side Only |
| `exports['meteo-apartments']:getCurrentComplex`          | Get current complex player is in              | Client side Only |
| `exports['meteo-apartments']:hasApartmentAccess`         | Check if player has access to apartment       | Client side Only |
| `exports['meteo-apartments']:OpenSpawnSelection`         | Open starter apartment selection menu         | Client side Only |
| `exports['meteo-apartments']:hasPermission`              | Check player permission for apartment         | Server side Only |
| `exports['meteo-apartments']:hasAccess`                  | Check if citizen has access to apartment      | Server side Only |
| `exports['meteo-apartments']:getPlayerApartments`        | Get all apartments player owns/has access to  | Server side Only |
| `exports['meteo-apartments']:createApartment`            | Create apartment for player (free)            | Server side Only |
| `exports['meteo-apartments']:spawnInsideApartment`       | Spawn player inside apartment                 | Server side Only |
| `exports['meteo-apartments']:getStartingComplexes`       | Get all starter apartment complexes           | Server side Only |
| `exports['meteo-apartments']:getAvailableApartments`     | Get available apartments in complex           | Server side Only |
| `exports['meteo-apartments']:getAvailableRoomCount`      | Get available room count for complex          | Server side Only |
| `exports['meteo-apartments']:getOwnedPropertiesForPhone` | Get owned apartments formatted for phone apps | Server side Only |

{% stepper %}
{% step %}
**getCurrentApartment**

Get current apartment player is in

Example

```lua
-- client-side
local apartment = exports['meteo-apartments']:getCurrentApartment()

if apartment then
    print('In apartment:', apartment.apartmentId)
    print('Complex:', apartment.complexId)
    print('Room:', apartment.roomNumber)
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table or nil</td><td>Apartment data { complexId, roomNumber, apartmentId } or nil if not in apartment</td></tr></tbody></table>

**Return Example:**

```lua
{
    complexId = 'wiwang_hotel',
    roomNumber = 6,
    apartmentId = 'wiwang_hotel_6'
}
-- OR nil if not in apartment
```
{% endstep %}

{% step %}
**isInsideApartment**

Check if player is inside apartment zone

Example

```lua
-- client-side
local isInside = exports['meteo-apartments']:isInsideApartment()

if isInside then
    print('Player is inside an apartment')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if inside apartment zone, false if outside</td></tr></tbody></table>
{% endstep %}

{% step %}
**getCurrentComplex**

Get current complex player is near (for elevators)

Example

```lua
-- client-side
local complexId = exports['meteo-apartments']:getCurrentComplex()

if complexId then
    print('Near complex:', complexId)
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>string or nil</td><td>Complex ID if near complex, nil if not</td></tr></tbody></table>
{% endstep %}

{% step %}
**hasApartmentAccess**

Check if player has access to specific apartment

Example

```lua
-- client-side
local hasAccess, isOwner = exports['meteo-apartments']:hasApartmentAccess('wiwang_hotel', 6)

if hasAccess then
    if isOwner then
        print('You own this apartment')
    else
        print('You are a member of this apartment')
    end
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>complexId</td><td>string</td><td>Yes</td><td>Complex identifier</td></tr><tr><td>roomNumber</td><td>number</td><td>Yes</td><td>Room number in complex</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean, boolean</td><td>hasAccess (true/false), isOwner (true/false)</td></tr></tbody></table>

**Return Example:**

```lua
-- Player owns the apartment
true, true

-- Player is a member (not owner)
true, false

-- No access
false, false
```
{% endstep %}

{% step %}
**OpenSpawnSelection**

Open the built-in starter apartment selection menu for new players

**Uses Meteo Apartments' built-in spawn selector** - no need to build your own UI.

Example

```lua
-- client-side
local success = exports['meteo-apartments']:OpenSpawnSelection()

if success then
    -- Spawn selection opened
    -- Player will choose apartment or default spawn
    -- Everything is handled automatically
else
    -- Failed to open (no starter complexes configured)
    print('No starter apartments available')
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if menu opened successfully, false if failed</td></tr></tbody></table>

**Return Example:**

```lua
-- Menu opened successfully
true

-- Failed (no starter complexes or player already has apartment)
false
```

**Notes**

This export handles everything automatically:

* Shows spawn selection UI
* Creates apartment FREE when player selects one
* Spawns player inside apartment
* Triggers clothing selection on first spawn

Perfect for multichar scripts. Just call this after character creation.
{% endstep %}

{% step %}
**hasPermission**

Check if player has specific permission for apartment

Example

```lua
-- server-side
local hasPermission = exports['meteo-apartments']:hasPermission(citizenid, apartmentId, 'furnish')

if hasPermission then
    print('Player can furnish this apartment')
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>citizenid</td><td>string</td><td>Yes</td><td>Player's citizenid</td></tr><tr><td>apartmentId</td><td>string</td><td>Yes</td><td>Apartment ID (e.g., "wiwang_hotel_6")</td></tr><tr><td>permission</td><td>string</td><td>Yes</td><td>Permission to check (furnish, door, invite, etc.)</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean</td><td>true if player has permission, false if not</td></tr></tbody></table>
{% endstep %}

{% step %}
**hasAccess**

Check if citizen has access to apartment (owner or member)

Example

```lua
-- server-side
local hasAccess, accessType = exports['meteo-apartments']:hasAccess(citizenid, apartmentId)

if hasAccess then
    if accessType == 'owner' then
        print('Player owns this apartment')
    else
        print('Player is a member')
    end
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>citizenid</td><td>string</td><td>Yes</td><td>Player's citizenid</td></tr><tr><td>apartmentId</td><td>string</td><td>Yes</td><td>Apartment ID (e.g., "wiwang_hotel_6")</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>boolean, string</td><td>hasAccess (true/false), accessType ('owner' or 'member')</td></tr></tbody></table>

**Return Example:**

```lua
-- Player owns the apartment
true, 'owner'

-- Player is a member
true, 'member'

-- No access
false, nil
```
{% endstep %}

{% step %}
**getPlayerApartments**

Get all apartments player owns or has access to

Example

```lua
-- server-side
local apartments = exports['meteo-apartments']:getPlayerApartments(citizenid)

for _, apt in ipairs(apartments) do
    print('Apartment:', apt.id, 'Owner:', apt.isOwner)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>citizenid</td><td>string</td><td>Yes</td><td>Player's citizenid</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table</td><td>Array of apartment data with isOwner field</td></tr></tbody></table>

**Return Example:**

```lua
{
    {
        id = 'wiwang_hotel_6',
        complexId = 'wiwang_hotel',
        roomNumber = 6,
        roomType = 'modern',
        citizenid = 'ABC12345',
        isOwner = true  -- Player owns this
    },
    {
        id = 'wiwang_hotel_12',
        complexId = 'wiwang_hotel',
        roomNumber = 12,
        roomType = 'modern',
        citizenid = 'XYZ67890',
        isOwner = false,  -- Player is a member
        permissions = { door = true, furnish = true }
    }
}
```
{% endstep %}

{% step %}
**createApartment**

Create apartment for player (free - used for starter apartments)

Example

```lua
-- server-side
local apartmentId, err = exports['meteo-apartments']:createApartment(source, complexId)

if not apartmentId then
    print('Failed to create apartment:', err)
else
    print('Created apartment:', apartmentId)
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>playerId</td><td>number</td><td>Yes</td><td>Player's server ID</td></tr><tr><td>complexId</td><td>string</td><td>Yes</td><td>Complex identifier</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>string, string</td><td>apartmentId (string) or nil, error (string) if failed</td></tr></tbody></table>

**Return Example:**

```lua
-- Success
'wiwang_hotel_6', nil

-- Failed - no available rooms
nil, 'no_available_apartments'

-- Failed - player already has apartment
nil, 'player_already_has_apartment'
```

**Notes**

This creates a FREE apartment (no money charged). Used for starter apartments. Finds first available room in complex and assigns it to player.
{% endstep %}

{% step %}
**spawnInsideApartment**

Spawn player inside their apartment

Example

```lua
-- server-side
exports['meteo-apartments']:spawnInsideApartment(source, apartmentId, true)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>playerId</td><td>number</td><td>Yes</td><td>Player's server ID</td></tr><tr><td>apartmentId</td><td>string</td><td>Yes</td><td>Apartment ID to spawn in</td></tr><tr><td>isFirstTime</td><td>boolean</td><td>No</td><td>If true, triggers clothing selection (default: false)</td></tr></tbody></table>

**Notes**

Handles everything: teleporting player to spawn point, triggering clothing selection on first spawn, and setting player state. Used for starter apartments and spawn selection.
{% endstep %}

{% step %}
**getStartingComplexes**

Get all complexes that allow starter apartments

Example

```lua
-- server-side
local complexes = exports['meteo-apartments']:getStartingComplexes()

for _, complex in ipairs(complexes) do
    print('Starter complex:', complex.id, complex.label)
end
```

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table</td><td>Array of complex data with startingEnabled = true</td></tr></tbody></table>

**Return Example:**

```lua
{
    {
        id = 'wiwang_hotel',
        label = 'WiWang Hotel',
        coords = vector3(-824.73, -702.12, 28.06),
        totalRooms = 20,
        availableRooms = 15,  -- Real-time count from database
        roomType = 'modern',
        startingEnabled = true
    },
    {
        id = 'another_complex',
        label = 'Downtown Apartments',
        coords = vector3(100.0, 200.0, 30.0),
        totalRooms = 10,
        availableRooms = 8,  -- Real-time count from database
        roomType = 'classic',
        startingEnabled = true
    }
}
```

**Complex Data Structure**

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Complex identifier</td></tr><tr><td>label</td><td>string</td><td>Display name</td></tr><tr><td>coords</td><td>vector3</td><td>Complex location</td></tr><tr><td>totalRooms</td><td>number</td><td>Total rooms configured in complex</td></tr><tr><td>availableRooms</td><td>number</td><td>Available (unowned) rooms - real-time from database</td></tr><tr><td>roomType</td><td>string</td><td>Room type (modern, classic, etc.)</td></tr></tbody></table>

**Notes**

The `availableRooms` field is automatically included with real-time counts from the database. Perfect for custom spawn selection menus.
{% endstep %}

{% step %}
**getAvailableApartments**

Get all available (unowned) apartments in a complex

Example

```lua
-- server-side
local available = exports['meteo-apartments']:getAvailableApartments('wiwang_hotel')

print('Available apartments:', #available)

for _, apt in ipairs(available) do
    print('Room', apt.roomNumber, 'is available')
end
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>complexId</td><td>string</td><td>Yes</td><td>Complex identifier</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table</td><td>Array of available apartment data (citizenid = NULL)</td></tr></tbody></table>

**Return Example:**

```lua
{
    {
        id = 'wiwang_hotel_1',
        complexId = 'wiwang_hotel',
        roomNumber = 1,
        roomType = 'modern',
        citizenid = nil,  -- Not owned
        floor = 1
    },
    {
        id = 'wiwang_hotel_3',
        complexId = 'wiwang_hotel',
        roomNumber = 3,
        roomType = 'modern',
        citizenid = nil,
        floor = 1
    }
    -- etc... only unowned apartments
}
```

**Notes**

Used for spawn selection menus and real-time availability checks. Only returns apartments that exist in config and are not currently owned.
{% endstep %}

{% step %}
**getAvailableRoomCount**

Get the count of available (unowned) rooms for a specific complex

Example

```lua
-- server-side
local count = exports['meteo-apartments']:getAvailableRoomCount('wiwang_hotel')

print('Available rooms in WiWang Hotel:', count)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>complexId</td><td>string</td><td>Yes</td><td>Complex identifier</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>number</td><td>Count of available (unowned) apartments in the complex</td></tr></tbody></table>

**Return Example:**

```lua
-- 15 apartments available in this complex
15

-- 0 if all apartments are owned or complex doesn't exist
0
```

**Notes**

This is useful for checking availability before showing a complex in your spawn selection menu. Real-time count from database.
{% endstep %}

{% step %}
**getOwnedPropertiesForPhone**

Get owned apartments formatted for phone app display. Returns data structured for easy integration with phone resources.



Example

```lua
-- server-side
local properties = exports['meteo-apartments']:getOwnedPropertiesForPhone(citizenid)

for _, property in ipairs(properties) do
    print('Property:', property.label, 'at', property.coords)
end
```



**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>citizenid</td><td>string</td><td>Yes</td><td>Player's citizenid</td></tr></tbody></table>

**Returns**

<table><thead><tr><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>table</td><td>Array of owned apartment data formatted for phone apps</td></tr></tbody></table>

**Return Example:**

```lua
{
    {
        id = 'wiwang_hotel_6',
        label = 'WiWang Hotel - Room 6',
        coords = vector3(-824.73, -702.12, 28.06),
        type = 'apartment',
        roomNumber = 6,
        complexId = 'wiwang_hotel',
        complexLabel = 'WiWang Hotel',
        roomType = 'modern'
    },
    {
        id = 'downtown_apts_12',
        label = 'Downtown Apartments - Room 12',
        coords = vector3(100.0, 200.0, 30.0),
        type = 'apartment',
        roomNumber = 12,
        complexId = 'downtown_apts',
        complexLabel = 'Downtown Apartments',
        roomType = 'classic'
    }
}
-- Returns empty table {} if no owned apartments
```

**Return Data Structure**

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Apartment ID (e.g., "wiwang_hotel_6")</td></tr><tr><td>label</td><td>string</td><td>Display name (Complex Label - Room #)</td></tr><tr><td>coords</td><td>vector3</td><td>Complex location coordinates</td></tr><tr><td>type</td><td>string</td><td>Always "apartment" for property type identification</td></tr><tr><td>roomNumber</td><td>number</td><td>Room number within complex</td></tr><tr><td>complexId</td><td>string</td><td>Complex identifier</td></tr><tr><td>complexLabel</td><td>string</td><td>Complex display name</td></tr><tr><td>roomType</td><td>string</td><td>Room type (modern, classic, etc.)</td></tr></tbody></table>

**Notes**

* Only returns apartments where the player is the **owner** (not member)
* Data is pre-formatted with labels for direct use in phone UIs
* The `type` field is always "apartment" to help distinguish from other property types (houses, garages, etc.)
{% endstep %}
{% endstepper %}

***

## Phone App Integration

Meteo Apartments provides a dedicated export for phone resources to display owned properties.

### Basic Integration

**Server-side callback for your phone resource:**

```lua
-- In your phone resource (server-side)
lib.callback.register('your-phone:server:getProperties', function(source)
    local Player = QBCore.Functions.GetPlayer(source)
    if not Player then return {} end

    local citizenid = Player.PlayerData.citizenid
    local properties = exports['meteo-apartments']:getOwnedPropertiesForPhone(citizenid)

    return properties
end)
```

**Client-side to fetch properties:**

```lua
-- In your phone resource (client-side)
local properties = lib.callback.await('your-phone:server:getProperties', false)

-- properties is ready to display in your phone UI
for _, property in ipairs(properties) do
    -- property.id = 'wiwang_hotel_6'
    -- property.label = 'WiWang Hotel - Room 6'
    -- property.coords = vector3(...)
    -- property.type = 'apartment'
end
```

### Setting Waypoint to Property

```lua
-- Client-side
local function setPropertyWaypoint(property)
    SetNewWaypoint(property.coords.x, property.coords.y)
    -- Notify player
    QBCore.Functions.Notify('GPS set to ' .. property.label, 'success')
end
```

### Full Phone App Example

Here's a complete example for a properties app in your phone resource:

**Server-side:**

```lua
local QBCore = exports['qb-core']:GetCoreObject()

lib.callback.register('your-phone:server:getPlayerProperties', function(source)
    local Player = QBCore.Functions.GetPlayer(source)
    if not Player then return { apartments = {} } end

    local citizenid = Player.PlayerData.citizenid

    -- Get apartments from meteo-apartments
    local apartments = {}
    if GetResourceState('meteo-apartments') == 'started' then
        apartments = exports['meteo-apartments']:getOwnedPropertiesForPhone(citizenid)
    end

    -- You can combine with other property resources here
    -- local houses = exports['your-housing']:getOwnedHouses(citizenid)

    return {
        apartments = apartments,
        -- houses = houses,
    }
end)
```

**Client-side:**

```lua
-- Fetch all properties for phone app
local function fetchProperties()
    local data = lib.callback.await('your-phone:server:getPlayerProperties', false)

    -- Send to NUI
    SendNUIMessage({
        action = 'updateProperties',
        apartments = data.apartments or {},
    })
end

-- NUI callback for setting waypoint
RegisterNUICallback('setPropertyWaypoint', function(data, cb)
    if data.coords then
        SetNewWaypoint(data.coords.x, data.coords.y)
        QBCore.Functions.Notify('GPS set', 'success')
    end
    cb({})
end)
```

**JavaScript (NUI):**

```javascript
// In your phone app
window.addEventListener('message', (event) => {
    if (event.data.action === 'updateProperties') {
        const apartments = event.data.apartments;

        apartments.forEach(apt => {
            // apt.id - unique identifier
            // apt.label - "WiWang Hotel - Room 6"
            // apt.coords - { x, y, z }
            // apt.type - "apartment"
            // apt.complexLabel - "WiWang Hotel"
            // apt.roomNumber - 6
            // apt.roomType - "modern"
        });
    }
});

// Set waypoint button click
function setWaypoint(property) {
    $.post(`https://${GetParentResourceName()}/setPropertyWaypoint`, JSON.stringify({
        coords: property.coords
    }));
}
```

### Data Structure Reference

The export returns an array where each property has:

| Field          | Example                            | Use Case                     |
| -------------- | ---------------------------------- | ---------------------------- |
| `id`           | `"wiwang_hotel_6"`                 | Unique key for lists         |
| `label`        | `"WiWang Hotel - Room 6"`          | Display in UI                |
| `coords`       | `vector3(-824.73, -702.12, 28.06)` | GPS waypoints                |
| `type`         | `"apartment"`                      | Filter/categorize properties |
| `complexLabel` | `"WiWang Hotel"`                   | Group by building            |
| `roomNumber`   | `6`                                | Sort rooms                   |
| `roomType`     | `"modern"`                         | Show property style          |

***

## Using with Custom Multichar Scripts

Meteo Apartments has a built-in spawn selection UI. Just call the export after character creation.

### Simple Integration

**Client-side (after character is created):**

```lua
-- In your multichar client-side code
-- After player creates a new character

local success = exports['meteo-apartments']:OpenSpawnSelection()

if success then
    -- Player will see apartment selection menu
    -- Meteo Apartments handles everything:
    -- - Shows available complexes
    -- - Creates apartment FREE
    -- - Spawns player inside
    -- - Triggers clothing selection
else
    -- Fallback to your default spawn
    YourDefaultSpawn()
end
```

**That's it.** The export opens the spawn selection UI, handles apartment creation, and spawns the player automatically.

### What OpenSpawnSelection() Does

1. Shows menu with available starter apartments
2. Player chooses an apartment or default spawn
3. Creates apartment FREE (no money charged)
4. Spawns player inside their apartment
5. Triggers clothing selection on first spawn

No need to build your own UI or handle apartment creation manually.

### Example: QBX Integration

This is exactly how the QBX integration works:

```lua
-- In qbx_core/client/character.lua
if config.characters.startingApartment then
    local success = exports['meteo-apartments']:OpenSpawnSelection()
    if not success then
        TriggerEvent('qbx_core:client:spawnNoApartments')
    end
else
    TriggerEvent('qbx_core:client:spawnNoApartments')
end
```

One line. Simple.

### Advanced: Manual Control (Server-Side)

If you need full control over the process (custom UI, custom flow), use these exports:

```lua
-- Get available complexes
local complexes = exports['meteo-apartments']:getStartingComplexes()

-- Get available rooms in a complex
local available = exports['meteo-apartments']:getAvailableApartments(complexId)

-- Create apartment for player (FREE)
local apartmentId, err = exports['meteo-apartments']:createApartment(source, complexId)

-- Spawn player inside
exports['meteo-apartments']:spawnInsideApartment(source, apartmentId, true)
```

But most developers should just use `OpenSpawnSelection()` - it's easier and handles everything.

{% hint style="info" %}
**Need help integrating?** Contact support on Discord: [http://discord.meteofivem.net/](http://discord.meteofivem.net/)

QBX integration is included by default. Custom multichar scripts can use `OpenSpawnSelection()` export.
{% endhint %}

***

## Support

For integration help, export questions, or custom multichar implementation:

* Discord: [Meteo Studios Discord](http://discord.meteofivem.net/)
