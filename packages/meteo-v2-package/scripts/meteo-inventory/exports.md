---
description: >-
  meteo-inventory exports - the full ox_inventory API under both resource
  names, plus the meteo additions for clothing slots, status tabs, backpacks
  and item notifications.
icon: code
---

# Exports

meteo-inventory is built on ox_inventory and keeps its whole export API. Every export answers under both names, so scripts written for ox_inventory work with no changes:

```lua
exports['meteo-inventory']:AddItem(source, 'water', 1)
exports.ox_inventory:AddItem(source, 'water', 1) -- same thing
```

The examples below use `exports['meteo-inventory']`. For the full argument lists of the standard exports, see the <a href="https://coxdocs.dev/ox_inventory" target="_blank">ox_inventory documentation</a>. This page covers the ones you will use most, and everything meteo-inventory adds on top.

***

## Server: Items

`inv` is a player server id or an inventory id (stash name, `'trunk' .. plate` and so on).

### AddItem(inv, item, count, metadata?, slot?, cb?)

Returns `success, response`. On failure `response` is the reason, e.g. `inventory_full`.

```lua
local ok, resp = exports['meteo-inventory']:AddItem(source, 'water', 2)

-- with metadata
exports['meteo-inventory']:AddItem(source, 'meteo_license', 1, { label = "Driver's License", durability = 100 })
```

### RemoveItem(inv, item, count, metadata?, slot?, ignoreTotal?, strict?)

Returns `success, response`.

```lua
local ok = exports['meteo-inventory']:RemoveItem(source, 'lockpick', 1)
```

### CanCarryItem(inv, item, count, metadata?)

Check this before you take money for an item.

```lua
if exports['meteo-inventory']:CanCarryItem(source, 'water', 5) then
    -- charge, then AddItem
end
```

`CanCarryAmount(inv, item)` returns how many more of an item fit. `CanCarryWeight(inv, weight)` checks a raw weight.

### GetItemCount(inv, itemName, metadata?, strict?)

```lua
local count = exports['meteo-inventory']:GetItemCount(source, 'lockpick')
print(count) --> 3
```

### Search(inv, search, items, metadata?)

`search` is `'count'` or `'slots'`. `items` is one name or a list.

```lua
local counts = exports['meteo-inventory']:Search(source, 'count', { 'water', 'sandwich' })
print(counts.water, counts.sandwich) --> 2  0
```

### GetSlot(inv, slot) / GetSlotWithItem(inv, itemName, metadata?, strict?)

```lua
local item = exports['meteo-inventory']:GetSlotWithItem(source, 'phone')
print(item.slot, item.metadata.serial)
```

Also available: `GetSlotIdWithItem`, `GetSlotsWithItem`, `GetSlotIdsWithItem`, `GetEmptySlot`, `GetSlotForItem`, `GetItem`, `SetItem`, `GetInventory`, `GetInventoryItems`, `GetCurrentWeapon`, `SwapSlots`.

### SetMetadata(inv, slot, metadata) / SetDurability(inv, slot, durability)

```lua
local item = exports['meteo-inventory']:GetSlotWithItem(source, 'drill')
item.metadata.durability = 60
exports['meteo-inventory']:SetMetadata(source, item.slot, item.metadata)
```

### Items(name?)

The item definition, or every item when called with no name. Also on the client.

```lua
local water = exports['meteo-inventory']:Items('water')
print(water.label, water.weight) --> Water  500
```

***

## Server: Stashes, Shops and Drops

### RegisterStash(name, label, slots, maxWeight, owner?, groups?, coords?)

`owner = true` gives every player their own copy. `groups` limits it to jobs, e.g. `{ police = 0 }`.

```lua
exports['meteo-inventory']:RegisterStash('pd_evidence', 'Evidence', 100, 500000, false, { police = 2 })
```

### CreateTemporaryStash(properties)

A one-off stash that is not saved. Returns its id. meteo-inventory adds `mystery = true`, which shows each slot covered with a "?" until the player clicks it.

```lua
local id = exports['meteo-inventory']:CreateTemporaryStash({
    label = 'Crate',
    slots = 5,
    maxWeight = 20000,
    items = { { 'water', 2 }, { 'lockpick', 1 } },
    mystery = true,
})
exports['meteo-inventory']:forceOpenInventory(source, 'stash', id)
```

### RegisterShop(shopType, shopDetails)

Same as ox_inventory. meteo-inventory adds `taxKind`: a tax key from the meteo-mdt tax list (e.g. `'shop_purchase'`). The rate the mayor set is charged on top, and the tax is paid through meteo-banking. Without the MDT the tax is `0`.

```lua
exports['meteo-inventory']:RegisterShop('hardware', {
    name = 'Hardware Store',
    taxKind = 'shop_purchase',
    inventory = {
        { name = 'lockpick', price = 150 },
    },
    locations = { vec3(45.6, -1748.4, 29.6) },
})
```

### forceOpenInventory(playerId, invType, data)

Opens an inventory for a player from the server.

```lua
exports['meteo-inventory']:forceOpenInventory(source, 'stash', 'pd_evidence')
```

Also available: `CustomDrop`, `CreateDropFromPlayer`, `ClearInventory`, `ConfiscateInventory`, `ReturnInventory`, `InspectInventory`, `RemoveInventory`, `SetMaxWeight`, `SetSlotCount`.

***

## Server: Hooks

### registerHook(event, cb, options?)

Runs your function before an inventory action. Return `false` to block it. Returns a hook id.

```lua
local hookId = exports['meteo-inventory']:registerHook('swapItems', function(payload)
    if payload.toInventory == 'pd_evidence' and payload.fromType == 'player' then
        return false
    end
end, {
    itemFilter = { lockpick = true },
})
```

Events: `swapItems`, `buyItem`, `craftItem`, `createItem`, `openInventory`, `openShop`, `usingItem`.

### removeHooks(id?)

Removes one hook, or every hook your resource registered when `id` is left out. Hooks are also removed when your resource stops.

```lua
exports['meteo-inventory']:removeHooks(hookId)
```

***

## Server: Clothing Slots

Worn clothing lives in its own slots in the inventory. Keys: `helmet`, `glasses`, `mask`, `ear`, `necklace`, `torso`, `bproof`, `watch`, `bag`, `pants`, `shoes`, `bracelet`, `decal`.

### IsClothingSystemEnabled()

Also on the client.

```lua
print(exports['meteo-inventory']:IsClothingSystemEnabled()) --> true
```

### UnequipClothing(src, keys)

Takes clothing off into the regular inventory. `keys` is one key or a list. Returns `ok, err, moved`.

```lua
local ok, err, moved = exports['meteo-inventory']:UnequipClothing(source, { 'mask', 'helmet' })
print(ok, err, moved) --> true  nil  2
```

Errors: `disabled`, `invalid`, `not_worn`.

### SyncClothingToSlots(src, appearance)

Rebuilds the clothing slots from an appearance table. Call it after your own script changes a player's outfit, so the slots match what they wear. meteo-appearance does this for you.

```lua
exports['meteo-inventory']:SyncClothingToSlots(source, appearance)
```

***

## Client

### openInventory(invType?, data?) / closeInventory()

```lua
exports['meteo-inventory']:openInventory('stash', 'pd_evidence')
exports['meteo-inventory']:closeInventory()
```

### openStatusTab(tab)

Opens the player's inventory on a Status sub tab. `tab` is `'effects'`, `'cravings'`, `'injuries'` or `'gym'`. Defaults to `'effects'`.

```lua
exports['meteo-inventory']:openStatusTab('gym')
```

### GetItemCount(itemName, metadata?, strict?) / Search(search, item, metadata?)

The client versions read the player's own inventory.

```lua
local count = exports['meteo-inventory']:GetItemCount('lockpick')
```

Also available: `GetPlayerItems`, `GetPlayerWeight`, `GetPlayerMaxWeight`, `GetSlotWithItem`, `GetSlotIdWithItem`, `GetSlotsWithItem`, `getCurrentWeapon`, `useItem`, `useSlot`, `giveItemToTarget`, `openNearbyInventory`, `displayMetadata`, `weaponWheel`, `setStashTarget`.

### suppressItemNotifications(value)

Hides the "item added / removed" pop-ups while `true`. Useful for a crafting or cooking step that moves a lot of items at once. Turn it back off when you are done.

```lua
exports['meteo-inventory']:suppressItemNotifications(true)
-- ...
exports['meteo-inventory']:suppressItemNotifications(false)
```

***

## Compatibility

meteo-inventory declares `provide 'ox_inventory'` and answers every export under the `ox_inventory` name too, so `exports.ox_inventory:...` calls from other scripts work as they are. The pefcl cash bridge (`addCash`, `removeCash`, `getCash`, `getCards`, `giveCard`) from ox_inventory is also kept.
