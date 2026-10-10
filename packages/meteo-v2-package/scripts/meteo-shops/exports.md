---
description: >-
  Every meteo-shops export with a simple example - list robbable branches and
  close a shop while it is being robbed.
icon: code
---

# Exports

Hook your own store robbery script into the shops. meteo-loosechange uses these to close a branch while it is robbed. Everything is server side.

A branch is marked robbable, with its registers and grabs, in the Shops creator in the admin menu.

***

## Robbable Branches

### GetRobbableShops()

Every branch marked robbable.

```lua
for _, shop in ipairs(exports['meteo-shops']:GetRobbableShops()) do
    print(shop.shopIdx, shop.locIdx, shop.label, #shop.registers)
end
--> 1   3   24/7 Supermarket   2
```

```lua
-- each branch:
{
    shopIdx   = 1,                                   -- shop type
    locIdx    = 3,                                   -- branch of that type
    coords    = vector4(25.7, -1347.3, 29.5, 270.0),
    label     = '24/7 Supermarket',
    registers = { vector4(...), vector4(...) },      -- {} if none placed
    grabs     = { vector4(...) },                    -- {} if none placed
}
```

`shopIdx` and `locIdx` are the keys the other two exports take.

***

## Closing a Shop

### SetShopDisabled(shopIdx, locIdx, disabled)

Closes or reopens one branch. Closing removes the clerk and the shop target for every online player, reopening brings them back. Not saved, so a restart reopens everything.

```lua
exports['meteo-shops']:SetShopDisabled(1, 3, true)   -- close during the robbery

SetTimeout(15 * 60000, function()
    exports['meteo-shops']:SetShopDisabled(1, 3, false)
end)
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `shopIdx` | number | From `GetRobbableShops` |
| `locIdx` | number | From `GetRobbableShops` |
| `disabled` | boolean | `true` closes, `false` reopens |

Returns nothing.

### IsShopDisabled(shopIdx, locIdx)

```lua
print(exports['meteo-shops']:IsShopDisabled(1, 3)) --> true
```
