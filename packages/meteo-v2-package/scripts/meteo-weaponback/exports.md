---
description: >-
  Every meteo-weaponback export with a simple example - refresh or clear the
  weapons on a player's back and start or stop carry items.
icon: code
---

# Exports

Control the weapons shown on the back and the carry items (boxes, trays) from your own scripts. Every export is client side and acts on the calling player.

***

## Weapons on Back

### RefreshWeaponsOnBack()

Rebuilds the weapons on the player's back from their inventory. Call it after your script changes something the back depends on, for example after putting away a shield or leaving an animation that hid the weapons.

```lua
exports['meteo-weaponback']:RefreshWeaponsOnBack()
```

### RemoveWeaponsOnBack()

Clears every weapon off the player's back.

```lua
exports['meteo-weaponback']:RemoveWeaponsOnBack()
```

This is not a lock. The weapons come back on the next inventory change, weapon swap or vehicle exit.

***

## Carry Items

Carry items are set in `Config.carryItems`. Normally they start on their own when the item sits in one of the slots listed for it. These exports let you start one yourself.

### StartCarrying(itemName)

Attaches the item's prop and plays its carry animation.

```lua
local ok = exports['meteo-weaponback']:StartCarrying('meteo_pizzathis')
print(ok) --> true
```

Returns `false` if the item has no entry in `Config.carryItems`, the player is dead, downed or cuffed, or the prop could not be created. Returns `true` straight away if they already carry that item.

The carry still follows the inventory, so on the next inventory change it stops again if the item is not in one of its carry slots.

### StopCarrying()

Removes the prop and stops the animation.

```lua
exports['meteo-weaponback']:StopCarrying()
```

### IsCarrying()

```lua
if exports['meteo-weaponback']:IsCarrying() then
    -- hands are full
end
```

### GetCarryItem()

The `Config.carryItems` entry being carried, or `nil`. This is the config table, not the item name.

```lua
local carry = exports['meteo-weaponback']:GetCarryItem()
if carry then
    print(carry.prop, carry.anim) --> prop_pizza_box_02   idle
end
```
