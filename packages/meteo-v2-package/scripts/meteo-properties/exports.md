---
description: >-
  Every meteo-properties export with a simple example and what it gives back -
  ownership and key checks, doors and locks, listings, apartments, rent and
  spawn points.
icon: code
---

# Exports

Read properties, check who has keys, lock doors and hand out apartment rooms from your own scripts. Almost everything is server side. The client exports only tell you where the local player is.

A property id is the number you see in the admin panel. Exports that need a player take a server id (`source`), the rest take a `citizenid`.

***

## Server: Properties

### GetProperty(id)

One property, or `nil`.

```lua
local p = exports['meteo-properties']:GetProperty(12)
print(p.label, p.ownerName, p.kind) --> 14 Grove Street   John Doe   shell
```

```lua
-- each property:
{
    id = 12,
    externalId = 'property_12',   -- the id meteo-garages and meteo-furnishing use
    label = '14 Grove Street',
    typeId = 1, typeKey = 'house',
    kind = 'shell',               -- shell | mlo
    price = 250000,
    forSale = false, saleMode = 'direct', hidden = false,
    ownerCid = 'ABC12345',        -- nil when nobody owns it
    ownerName = 'John Doe',
    entrance = { x, y, z, w },
    street = 'Grove Street', zoneName = 'Davis',
    garage = { x, y, z, w },      -- nil when it has no garage
    images = { 'https://...' },
    security = 2, locked = true,
    complexId = nil,              -- set when this is an apartment room
    roomNumber = nil,
    doors = { { id, label, type, center = { x, y, z }, ... } },
    roles = { ... },
    members = { { citizenid, name, roleId, roleLabel } },
}
```

### GetProperties()

Every property, same shape as above.

```lua
local all = exports['meteo-properties']:GetProperties()
print(#all) --> 84
```

### GetPropertiesByType(typeKey)

```lua
local warehouses = exports['meteo-properties']:GetPropertiesByType('warehouse')
```

Returns `{}` if the type key does not exist.

### GetPropertyType(typeKey) / GetPropertyTypes()

```lua
local t = exports['meteo-properties']:GetPropertyType('house')
print(t.label, t.memberLimit, t.garageAllowed) --> House   5   true
```

`GetPropertyTypes` returns every type.

### GetOwnedProperties(citizenid)

Only the properties this citizen owns, not the ones they have keys to.

```lua
for _, p in ipairs(exports['meteo-properties']:GetOwnedProperties('ABC12345')) do
    print(p.id, p.label, p.type)
end
--> 12   14 Grove Street               property
--> 40   Wiwang Hotel - Room 104       apartment
```

```lua
-- each entry:
{
    id = 12, label = '14 Grove Street',
    coords = vector3(...),        -- the entrance
    type = 'property',            -- property | apartment
    kind = 'shell', typeKey = 'house', typeLabel = 'House',
    complexId = nil, complexLabel = nil, roomNumber = nil,
}
```

### GetPropertyOwner(id)

The owner's citizenid, or `nil`.

```lua
print(exports['meteo-properties']:GetPropertyOwner(12)) --> ABC12345
```

***

## Server: Access and Permissions

The owner always has access. A member (keyholder) has access, and when you pass a `permission` their role must also allow it.

Built in permissions: `door`, `garage`, `stash`, `wardrobe`, `furnish`, `photos`, `upgrades`, `manage_members`, `manage_roles`, `view_logs`.

### HasPropertyAccess(src, id, permission?)

```lua
if exports['meteo-properties']:HasPropertyAccess(source, 12) then
    -- owner or keyholder
end

local canUseStash = exports['meteo-properties']:HasPropertyAccess(source, 12, 'stash')
```

Returns `true` or `false`.

### HasAccessByCitizenId(citizenid, id, permission?)

Same check for an offline player.

```lua
print(exports['meteo-properties']:HasAccessByCitizenId('ABC12345', 12, 'garage')) --> true
```

### RegisterPropertyPermission(key, label)

Adds your own permission to the role editor, so owners can tick it per role. `key` is lowercase `a-z`, `0-9` and `_`. `label` is a locale key or plain text.

```lua
exports['meteo-properties']:RegisterPropertyPermission('meth_lab', 'Use the meth lab')

-- later
if exports['meteo-properties']:HasPropertyAccess(source, propertyId, 'meth_lab') then
    -- allowed
end
```

Returns `true`, or `false` if the key is invalid. A permission that was never registered is never granted to a member.

### GetStorageLimit(id) / GetFurnitureLimit(id)

The current stash and furniture limits after upgrades and perks.

```lua
print(exports['meteo-properties']:GetStorageLimit(12))   --> 200000
print(exports['meteo-properties']:GetFurnitureLimit(12)) --> 150
```

***

## Server: Inside a Property

### IsPlayerInside(src)

The property id the player is inside, or `nil`.

```lua
local id = exports['meteo-properties']:IsPlayerInside(source)
if id then print('inside', id) end
```

### GetPlayersInside(id)

Server ids of everyone inside, sorted.

```lua
local players = exports['meteo-properties']:GetPlayersInside(12)
print(#players) --> 2
```

### GetPropertyBucket(id)

The routing bucket a shell property uses, or `nil` for an MLO.

```lua
print(exports['meteo-properties']:GetPropertyBucket(12)) --> 100012   (Config.bucketBase + id)
```

***

## Server: Doors and Locks

### SetPropertyLocked(id, locked)

Locks or unlocks the whole property (the shell door, or every door of an MLO).

```lua
exports['meteo-properties']:SetPropertyLocked(12, false)
```

Returns `true`, or `false` if the property does not exist.

### SetDoorLocked(doorId, locked) / GetDoorLocked(doorId)

One door of an MLO. Door ids come from `GetProperty(id).doors`.

```lua
exports['meteo-properties']:SetDoorLocked(31, true)
print(exports['meteo-properties']:GetDoorLocked(31)) --> true
```

`GetDoorLocked` returns `nil` if the door does not exist.

***

## Server: Listings and Sales

### GetListings(query?)

Search the properties for sale, paged. Hidden listings are never returned.

```lua
local res = exports['meteo-properties']:GetListings({
    q = 'grove',           -- optional, free text
    typeKey = 'house',     -- optional
    kind = 'shell',        -- optional, shell | mlo
    priceMin = 50000,      -- optional
    priceMax = 300000,     -- optional
    garage = 'yes',        -- optional, any | yes | no
    seller = 'city',       -- optional, any | city | owner
    mode = 'direct',       -- optional, any | direct | agent
    sort = 'price',        -- optional, newest | price | label
    dir = 'asc',           -- optional, asc | desc
    page = 1,
    pageSize = 12,         -- 10 to 50
})

print(res.total, #res.items) --> 7   7
print(res.items[1].label, res.items[1].price) --> 14 Grove Street   250000
```

### GetListing(id)

The full listing for one property, or `nil` if it is not for sale.

```lua
local l = exports['meteo-properties']:GetListing(12)
print(l.price, l.saleMode, l.canBuyAtDoor) --> 250000   direct   true
```

### GetListedProperties()

Every visible listing, without paging.

```lua
local forSale = exports['meteo-properties']:GetListedProperties()
```

### SetPropertyHidden(id, hidden)

Hides a listing from the realtor app and the map without taking it off the market.

```lua
exports['meteo-properties']:SetPropertyHidden(12, true)
```

Returns `true` or `false`.

### PurchaseProperty(src, id, payment)

Buys a `direct` listing for the player at its list price. `payment` is `'bank'` or `'cash'` and must be allowed in `Config.realestate.doorAccounts`. This export does not check distance, so do that yourself if it matters.

```lua
local res = exports['meteo-properties']:PurchaseProperty(source, 12, 'bank')
if res.ok then
    print('bought for', res.price)
else
    print(res.error) --> insufficient_funds
end
```

Errors include `player_not_found`, `not_found`, `not_listed`, `agent_only`, `invalid_data`, `insufficient_funds`, `sale_busy`.

***

## Server: Apartments

Apartment rooms are properties too, so every export above works on a room id. These return `nil` or `{}` while `Config.apartments.enabled` is off.

### GetComplexes() / GetComplex(id)

```lua
local cx = exports['meteo-properties']:GetComplex(1)
print(cx.label, cx.rent, cx.starter) --> Wiwang Hotel   150   true
```

### IsRoom(id) / GetRoom(id) / GetRoomByNumber(complexId, number)

```lua
print(exports['meteo-properties']:IsRoom(40)) --> true

local room = exports['meteo-properties']:GetRoomByNumber(1, 104)
print(room.id, room.ownerCid) --> 40   ABC12345
```

`GetRoom` and `GetRoomByNumber` return the same shape as `GetProperty`.

### GetRoomLabel(id)

```lua
print(exports['meteo-properties']:GetRoomLabel(40)) --> Wiwang Hotel - Room 104
```

### GetPlayerRooms(citizenid, purpose?)

The rooms this citizen rents. Pass `'spawn'` to get `{}` when `Config.spawn` is turned off.

```lua
for _, r in ipairs(exports['meteo-properties']:GetPlayerRooms('ABC12345')) do
    print(r.spawnLabel, r.coords)
end
--> Wiwang Hotel - Room 104   vector4(...)
```

```lua
-- each room:
{
    id = 40, label = 'Room 104',
    complexId = 1, complexLabel = 'Wiwang Hotel',
    roomNumber = 104, floor = 1,
    spawnLabel = 'Wiwang Hotel - Room 104',
    coords = vector4(...),        -- inside spawn
    entrance = { x, y, z, w },
}
```

### GetRentStatus(id)

`nil` when the room has no rent.

```lua
local rent = exports['meteo-properties']:GetRentStatus(40)
print(rent.amount, rent.dueAt, rent.missed) --> 150   1782364949000   0
```

`dueAt` is epoch ms. `cycleDays` is also returned.

***

## Server: Spawning and Multicharacter

For a spawn selector or multicharacter script.

### GetSpawnPoints(citizenid)

Properties this citizen owns, then ones they hold keys to (if `Config.spawn.keyholders` is on), capped at `Config.spawn.maxEntries`. Returns `{}` when `Config.spawn.enabled` is off.

```lua
for _, s in ipairs(exports['meteo-properties']:GetSpawnPoints('ABC12345')) do
    print(s.id, s.label, s.tag)
end
--> 12   Grove House - Grove Street   owned
--> 33   Vinewood Loft                    key
```

```lua
-- each entry:
{ id = 12, label = 'Grove House - Grove Street', kind = 'shell', tag = 'owned', room = false, coords = vector4(...) }
```

### SpawnAtProperty(src, id, callerTeleports?)

Rechecks access, then spawns the player there. A shell puts them inside it. For an MLO or room the player is moved for you, unless you pass `callerTeleports = true` and move them yourself to `res.coords`.

```lua
local res = exports['meteo-properties']:SpawnAtProperty(source, 12)
print(res.ok, res.tag, res.shell) --> true   owned   true
```

Errors: `unavailable`, `not_found`, `no_permission`, `player_not_found`.

### GetStarterComplexes()

Complexes marked as starter with free rooms left.

```lua
for _, cx in ipairs(exports['meteo-properties']:GetStarterComplexes()) do
    print(cx.id, cx.label, cx.availableRooms)
end
--> 1   Wiwang Hotel   38
```

### ClaimStarterRoom(src, complexId)

Gives a new character the lowest free room in a starter complex, for free. Fails if they already have a room.

```lua
local res = exports['meteo-properties']:ClaimStarterRoom(source, 1)
if res.ok then
    print(res.id, res.label, res.number) --> 40   Room 104   104
end
```

Errors: `unavailable`, `not_ready`, `not_found`, `complex_full`, `room_limit`, `player_not_found`.

### SpawnInsideRoom(src, id, firstTime?)

Puts a tenant or keyholder inside their room. Returns `false` if they have no access.

```lua
local res = exports['meteo-properties']:ClaimStarterRoom(source, 1)
if res.ok then
    exports['meteo-properties']:SpawnInsideRoom(source, res.id, true)
end
```

***

## Client

### IsInsideProperty()

```lua
if exports['meteo-properties']:IsInsideProperty() then
    -- no weather sync, no NPC spawns, etc.
end
```

### GetCurrentProperty()

```lua
local cur = exports['meteo-properties']:GetCurrentProperty()
print(cur.id, cur.kind, cur.label) --> 12   shell   14 Grove Street
--> nil when outside
```

### GetNearbyProperties(radius?)

Properties around the player, closest first. `radius` defaults to `Config.loadRadius`.

```lua
for _, p in ipairs(exports['meteo-properties']:GetNearbyProperties(50.0)) do
    print(p.label, p.distance, p.forSale, p.mine)
end
```

```lua
-- each entry:
{
    id = 12, typeId = 1, kind = 'shell', label = '14 Grove Street',
    entrance = { x, y, z, w }, distance = 12.4,
    forSale = false, agentOnly = false, owned = true,
    mine = true,         -- the player owns it or holds keys
    complexId = nil,
}
```

### IsLoaded()

`true` once the client has received the property list. Check it before `GetNearbyProperties` right after joining.

```lua
while not exports['meteo-properties']:IsLoaded() do Wait(250) end
```

***

## Events

Server side events you can listen to.

```lua
AddEventHandler('meteo-properties:server:playerEntered', function(src, propertyId, kind) end) -- kind: shell | mlo
AddEventHandler('meteo-properties:server:playerLeft', function(src, propertyId, kind) end)
AddEventHandler('meteo-properties:server:lockChanged', function(data) end)   -- { propertyId, locked, cids }
AddEventHandler('meteo-properties:server:propertySold', function(data) end)  -- { propertyId, label, mode, buyerCid, sellerCid, price, payment, ... }
AddEventHandler('meteo-properties:server:roomClaimed', function(data) end)   -- { propertyId, complexId, roomNumber, cid, src, starter, price }
AddEventHandler('meteo-properties:server:roomVacated', function(data) end)   -- { propertyId, complexId, cid, reason }
AddEventHandler('meteo-properties:server:rentPaid', function(data) end)      -- { propertyId, cid, amount, dueAt }
AddEventHandler('meteo-properties:server:rentMissed', function(data) end)    -- { propertyId, cid, amount, missed }
```

***

## Older Export Names

Kept so older scripts keep working. New code should use the names above.

| Old name | Same as |
| -------- | ------- |
| `hasPlayerAccess(src, id, perm?)` | `HasPropertyAccess` |
| `hasAccess(cid, id)` | `HasAccessByCitizenId` without a permission |
| `hasPermission(cid, id, perm)` / `hasPropertyPermission(cid, id, perm)` | `HasAccessByCitizenId` |
| `getOwner(id)` | `GetPropertyOwner` |
| `getOwnedPropertiesForPhone(cid)` | `GetOwnedProperties` |
| `getStorageLimit(id)` | `GetStorageLimit` |
| `GetPropertiesForSale()` | `GetListedProperties` |
| `getPropertyById(id)` | `GetProperty`, plus the old fields `name`, `owner`, `property_type`, `coords` |
| `getPlayerProperties(cid)` | Owned and keyed properties in the old shape above |
