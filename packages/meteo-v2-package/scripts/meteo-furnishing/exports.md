---
description: >-
  Every meteo-furnishing export with a simple example and what it gives back -
  loading furniture, the placement menu, the external editor, storage stashes
  and the catalog.
icon: code
---

# Exports

Load and edit furniture from your own scripts, reuse the placement editor for your own props, and read placed pieces server side.

meteo-properties already calls these for you. You only need them for your own housing script, a creator tool, or a script that hooks into placed furniture (a crafting bench, a meth lab).

A property id is a string. meteo-properties uses `'property_' .. id`, for example `'property_12'`. The placement menu only grants permission for ids in that format, checked against the meteo-properties `furnish` permission.

***

## Client: Furniture

### LoadFurniture(propertyId, propertyType, shellOrigin?)

Spawns the saved furniture for a property and starts live sync for it. Call it when the player enters.

```lua
local origin = vector3(0.0, 0.0, -50.0) -- shell origin, only for shells
local entities = exports['meteo-furnishing']:LoadFurniture('property_12', 'shell', origin)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `propertyId` | string | e.g. `'property_12'` |
| `propertyType` | string | `'shell'` or `'mlo'` |
| `shellOrigin` | vector3 | Shells only. Saved coords are offsets from it |

Returns a table of `furnitureId -> entity`.

### UnloadFurniture(propertyId)

Deletes the spawned furniture and stops live sync. Call it when the player leaves.

```lua
exports['meteo-furnishing']:UnloadFurniture('property_12')
```

### OpenMenu(propertyId, propertyType, shellOrigin?, bounds?, furnitureLimit?)

Opens the placement editor. Returns `true` if it opened, `false` if the player is outside `bounds` or has no permission (both show a notification).

```lua
exports['meteo-furnishing']:OpenMenu('property_12', 'mlo', nil, {
    type = 'poly',
    points = { vec3(10.0, 20.0, 30.0), vec3(25.0, 20.0, 30.0), vec3(25.0, 40.0, 30.0) },
    minZ = 29.0,
    maxZ = 36.0,
}, 150)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `propertyId` | string | `'property_<id>'` |
| `propertyType` | string | `'shell'` or `'mlo'`, default `'mlo'` |
| `shellOrigin` | vector3 | Shells only |
| `bounds` | table | Optional. The player and the camera must stay inside it |
| `furnitureLimit` | number | Default `Config.defaultFurnitureLimit` |

### GetFurniture(propertyId)

Every saved piece in a property, fetched from the server.

```lua
for _, f in ipairs(exports['meteo-furnishing']:GetFurniture('property_12')) do
    print(f.id, f.itemId, f.model)
end
--> 881   v_res_fh_sofa   v_res_fh_sofa
```

```lua
-- each piece:
{
    id = 881, itemId = 'v_res_fh_sofa', model = 'v_res_fh_sofa',
    coords = { x, y, z },       -- offset from the shell origin for shells
    rotation = { x, y, z },
    placedBy = 'ABC12345',
}
```

### GetFurnitureEntity(propertyId, furnitureId)

The spawned entity for one piece, or `nil` if it is not loaded.

```lua
local entity = exports['meteo-furnishing']:GetFurnitureEntity('property_12', 881)
```

### DeleteFurniture(furnitureId, propertyId)

Removes a piece without a refund. Returns `true` or `false`.

```lua
exports['meteo-furnishing']:DeleteFurniture(881, 'property_12')
```

***

## Client: External Editor

Reuse the catalog, freecam and gizmo for your own props (a robbery creator, a decoration tool). Nothing is saved by meteo-furnishing. Every place, move and delete is handed back to your callbacks, and you store it yourself.

### OpenExternalEditor(opts)

Returns `true`, or `false` if a furnishing session is already open.

```lua
exports['meteo-furnishing']:OpenExternalEditor({
    title = 'Loot Spots',
    categories = {
        { id = 'loot', label = 'Loot', icon = 'box', items = {
            { id = 'safe', label = 'Safe', model = 'prop_ld_int_safe_01' },
        } },
    },
    existing = {                     -- optional, preloaded as editable
        { id = 'spot_1', model = 'prop_ld_int_safe_01', label = 'Safe', coords = vec3(1.0, 2.0, 3.0), rotation = vec3(0.0, 0.0, 90.0) },
    },
    freecamMaxDistance = 50.0,       -- optional, default 50.0
    onPlaced = function(itemId, coords, rotation)
        return 'spot_' .. math.random(1000, 9999) -- your id for the new prop
    end,
    onMoved = function(externalId, coords, rotation) return true end,
    onDeleted = function(externalId) return true end,
    onClosed = function() end,
})
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `title` | string | Shown in the editor header |
| `categories` | table | `{ { id, label, icon, items = { { id, label, model } } } }`. Use `GetCatalogCategories()` to offer the normal furniture |
| `existing` | table | Props you already placed, `{ { id, model, label, coords, rotation } }` |
| `onPlaced` | function | Return your id for the new prop |
| `onMoved` / `onDeleted` | function | Return `true` to accept |
| `onCustomModel` | function | Optional. Return `{ id, label, model }` to add a custom model from the catalog's + button |
| `onClosed` | function | Called when the editor closes |

### CloseExternalEditor() / IsExternalEditorOpen()

```lua
if exports['meteo-furnishing']:IsExternalEditorOpen() then
    exports['meteo-furnishing']:CloseExternalEditor()
end
```

### GetCatalogCategories()

The furniture catalog, ready to pass as `categories`.

```lua
local cats = exports['meteo-furnishing']:GetCatalogCategories()
print(cats[1].label, #cats[1].items) --> Living Room   42
```

***

## Server: Placed Furniture

### GetFurniturePiece(furnitureId)

One placed piece, read from the database, or `nil`.

```lua
local piece = exports['meteo-furnishing']:GetFurniturePiece(881)
print(piece.model, piece.propertyId, piece.propertyType) --> v_res_fh_sofa   property_12   mlo
```

```lua
{
    id = 881,
    model = 'v_res_fh_sofa',     -- the catalog item id
    propertyId = 'property_12',
    propertyType = 'mlo',
    coords = vector3(...),       -- nil for shells, they have no fixed world position
}
```

### PlayerCanUseFurniture(src, furnitureId, permission?)

Does the player have the meteo-properties permission for the property this piece is in. `permission` defaults to `door`.

```lua
if exports['meteo-furnishing']:PlayerCanUseFurniture(source, 881, 'stash') then
    -- let them use it
end
```

### ClearProperty(propertyId)

Deletes every piece in a property and empties its storage stashes. Players inside see the props disappear.

```lua
local ok = exports['meteo-furnishing']:ClearProperty('property_12')
```

Returns `true` or `false`.

### GetAllProps()

The whole catalog as one flat list.

```lua
for _, p in ipairs(exports['meteo-furnishing']:GetAllProps()) do
    print(p.model, p.label, p.price, p.categoryLabel)
end
```

***

## Server: Storage Stashes

For an eviction or repossession script that lets the old owner collect what was left in their storage furniture.

### getStorageStashes(propertyId)

Every storage piece in a property and the stash it owns.

```lua
for _, s in ipairs(exports['meteo-furnishing']:getStorageStashes('property_12')) do
    print(s.stashId, s.label)
end
--> furnishing_property_12_881   Wardrobe Safe
```

Each entry: `{ stashId, furnitureId, itemId, label }`.

### prepareClaimStash(stashId, itemId?, label?)

Registers the stash at a size that fits its contents and returns how many items are still in it.

```lua
local left = exports['meteo-furnishing']:prepareClaimStash(s.stashId, s.itemId, s.label)
print(left) --> 4
```

### openClaimStash(src, stashId, itemId?, label?)

Opens the stash for a player and returns `true, itemsLeft`. It does no access check, so check ownership first.

```lua
local ok, left = exports['meteo-furnishing']:openClaimStash(source, s.stashId, s.itemId, s.label)
```
