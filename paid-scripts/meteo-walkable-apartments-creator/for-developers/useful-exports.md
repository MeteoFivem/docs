# Useful Exports

## Quick Exports Reference Table

| Export | Purpose | Side |
| ----------------------------------------------- | ------------------------- | ---------------- |
| `exports['meteo-apartments']:getCurrentApartment` | Get current apartment player is in | Client side Only |
| `exports['meteo-apartments']:isInsideApartment` | Check if player is inside apartment | Client side Only |
| `exports['meteo-apartments']:getCurrentComplex` | Get current complex player is in | Client side Only |
| `exports['meteo-apartments']:hasApartmentAccess` | Check if player has access to apartment | Client side Only |
| `exports['meteo-apartments']:hasPermission` | Check player permission for apartment | Server side Only |
| `exports['meteo-apartments']:hasAccess` | Check if citizen has access to apartment | Server side Only |
| `exports['meteo-apartments']:getPlayerApartments` | Get all apartments player owns/has access to | Server side Only |
| `exports['meteo-apartments']:createApartment` | Create apartment for player (free) | Server side Only |
| `exports['meteo-apartments']:spawnInsideApartment` | Spawn player inside apartment | Server side Only |
| `exports['meteo-apartments']:getStartingComplexes` | Get all starter apartment complexes | Server side Only |
| `exports['meteo-apartments']:getAvailableApartments` | Get available apartments in complex | Server side Only |

{% stepper %}
{% step %}
#### getCurrentApartment

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
#### isInsideApartment

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
#### getCurrentComplex

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
#### hasApartmentAccess

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
#### hasPermission

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
#### hasAccess

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
#### getPlayerApartments

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
#### createApartment

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

This creates a FREE apartment (no money charged). Used for starter apartment systems. Finds first available room in complex and assigns it to player.
{% endstep %}

{% step %}
#### spawnInsideApartment

Spawn player inside their apartment

Example

```lua
-- server-side
exports['meteo-apartments']:spawnInsideApartment(source, apartmentId, true)
```

**Parameters**

<table><thead><tr><th width="120">Parameter</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>playerId</td><td>number</td><td>Yes</td><td>Player's server ID</td></tr><tr><td>apartmentId</td><td>string</td><td>Yes</td><td>Apartment ID to spawn in</td></tr><tr><td>isFirstTime</td><td>boolean</td><td>No</td><td>If true, triggers clothing selection (default: false)</td></tr></tbody></table>

**Notes**

Handles everything: teleporting player to spawn point, triggering clothing selection on first spawn, and setting player state. Used for starter apartments and spawn selection systems.
{% endstep %}

{% step %}
#### getStartingComplexes

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
        roomType = 'modern',
        startingEnabled = true
    },
    {
        id = 'another_complex',
        label = 'Downtown Apartments',
        coords = vector3(100.0, 200.0, 30.0),
        roomType = 'classic',
        startingEnabled = true
    }
}
```

**Complex Data Structure**

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Complex identifier</td></tr><tr><td>label</td><td>string</td><td>Display name</td></tr><tr><td>coords</td><td>vector3</td><td>Complex location</td></tr><tr><td>roomType</td><td>string</td><td>Room type (modern, classic, etc.)</td></tr></tbody></table>
{% endstep %}

{% step %}
#### getAvailableApartments

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
{% endstepper %}

***

## Implementing Multichar with Starter Apartments

If you're a developer building a custom multicharacter system and want to integrate Meteo Apartments starter apartment selection, here's how:

### Server-Side Implementation Example

```lua
-- In your multichar server-side code

-- When player selects "Create Character"
RegisterNetEvent('your-multichar:server:createCharacter', function(charData)
    local source = source
    local citizenid = charData.citizenid

    -- Check if player selected an apartment (complexId from client)
    local selectedComplexId = charData.apartmentComplexId

    if selectedComplexId then
        -- Player chose an apartment - create it FREE
        local apartmentId, err = exports['meteo-apartments']:createApartment(source, selectedComplexId)

        if apartmentId then
            -- Spawn player inside their new apartment
            exports['meteo-apartments']:spawnInsideApartment(source, apartmentId, true)
            -- isFirstTime = true triggers clothing selection
        else
            -- Failed to create apartment - use default spawn
            print('Failed to create apartment:', err)
            SpawnAtDefaultLocation(source)
        end
    else
        -- Player chose default spawn
        SpawnAtDefaultLocation(source)
    end
end)
```

### Client-Side Menu Example

```lua
-- In your multichar client-side code

-- Get available starter complexes
local function GetStarterComplexes()
    -- Fetch complexes with real-time availability
    local complexes = lib.callback.await('your-multichar:server:getStarterComplexes', false)
    return complexes
end

-- Server callback to get complexes
lib.callback.register('your-multichar:server:getStarterComplexes', function(source)
    local complexes = exports['meteo-apartments']:getStartingComplexes()

    -- Add real-time availability count
    for i, complex in ipairs(complexes or {}) do
        local available = exports['meteo-apartments']:getAvailableApartments(complex.id)
        complex.availableRooms = #available
    end

    return complexes
end)

-- Show in your character creation menu
local function ShowApartmentSelection()
    local complexes = GetStarterComplexes()

    -- Build your menu options
    local options = {
        {
            label = 'Default Spawn',
            value = nil  -- No apartment
        }
    }

    for _, complex in ipairs(complexes) do
        if complex.availableRooms > 0 then
            options[#options + 1] = {
                label = complex.label .. ' (' .. complex.availableRooms .. ' available)',
                value = complex.id
            }
        end
    end

    -- Show your menu and get selection
    -- Return selected complexId or nil
end
```

### Anti-Cheat Example

```lua
-- Server-side validation before creating apartment
local function CanCreateStarterApartment(source, citizenid, complexId)
    -- Check if player already has apartment
    local existingApartments = exports['meteo-apartments']:getPlayerApartments(citizenid)
    if existingApartments and #existingApartments > 0 then
        return false, 'already_has_apartment'
    end

    -- Validate complex is a starter complex
    local startingComplexes = exports['meteo-apartments']:getStartingComplexes()
    local validComplex = false

    for _, complex in ipairs(startingComplexes or {}) do
        if complex.id == complexId then
            validComplex = true
            break
        end
    end

    if not validComplex then
        return false, 'invalid_complex'
    end

    -- Check if complex has available rooms
    local available = exports['meteo-apartments']:getAvailableApartments(complexId)
    if #available == 0 then
        return false, 'no_rooms_available'
    end

    return true, nil
end
```

{% hint style="info" %}
**Need help integrating with your multichar?** Contact support on Discord: [http://discord.meteofivem.net/](http://discord.meteofivem.net/)

The QBX integration is included by default. Custom multichar systems require custom integration using these exports.
{% endhint %}

***

## Support

For integration help, export questions, or custom multichar implementation:

* Discord: [Meteo Studios Discord](http://discord.meteofivem.net/)
