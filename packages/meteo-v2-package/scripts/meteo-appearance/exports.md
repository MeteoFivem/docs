---
description: >-
  Every meteo-appearance export with a simple example and what it gives back -
  opening the menu, reading and applying appearances, tattoos and admin custom
  peds.
icon: code
---

# Exports

Open the appearance menu, read or apply a player's look, and give players a custom ped from your own scripts.

Client exports act on the calling player (or a ped you pass in). Server exports take a citizenid.

***

## Client: Menus

### openMenu(config, callback?)

Opens the appearance menu. Does nothing if it is already open. The new look is saved when the player confirms. Cancelling puts the old look back.

```lua
exports['meteo-appearance']:openMenu({
    shopType = 'clothing',
    sections = {
        components = true,
        props = true,
        outfit = true,
    },
}, function(appearance)
    if appearance then
        -- saved
    else
        -- cancelled
    end
end)
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `shopType` | string | `clothing`, `barber`, `tattoo`, `surgeon`, `outfit`, `character` or `all`. Paid types charge `Config.costs[shopType]` on save. `character`, `outfit` and `all` are free |
| `sections` | table | Which tabs show: `ped`, `headBlend`, `faceFeatures`, `headOverlays`, `components`, `props`, `tattoos`, `hair`, `outfit`, `outfits`. Copy one of `Config.clothingSections`, `barberSections`, `tattooSections`, `surgeonSections`, `outfitSections` to match a shop |
| `chargePerTattoo` | boolean | Optional, defaults to `Config.chargePerTattoo` |

The callback gets the saved appearance table, or `nil` if the player cancelled.

### openCharacterCreation(callback?)

The new character flow. Reads the gender from the player's charinfo, dresses them in `Config.initialPlayerClothes`, moves them to a private routing bucket and opens the full creator.

```lua
exports['meteo-appearance']:openCharacterCreation(function(appearance)
    -- appearance on save, nil on cancel
end)
```

### initializeCharacter(gender, onSubmit?, onCancel?)

Same as `openCharacterCreation`, but you pick the gender.

```lua
exports['meteo-appearance']:initializeCharacter('female', function(appearance)
    -- created
end, function()
    -- cancelled
end)
```

`gender` is `'male'` or `'female'`.

***

## Client: The Player's Appearance

### getAppearance()

The current look of the calling player.

```lua
local appearance = exports['meteo-appearance']:getAppearance()
print(appearance.model) --> mp_m_freemode_01
```

```lua
-- appearance table:
{
    model        = 'mp_m_freemode_01',
    headBlend    = { shapeFirst, shapeSecond, shapeThird, skinFirst, skinSecond, skinThird, shapeMix, skinMix, thirdMix },
    faceFeatures = { nose_width = 0.0, ... },
    headOverlays = { beard = { style, opacity, color, secondColor }, ... },
    components   = { { component_id = 11, drawable = 15, texture = 0 }, ... },
    props        = { { prop_id = 0, drawable = -1, texture = 0 }, ... },
    hair         = { style = 4, color = 0, highlight = 0, texture = 0, fade = 0 },
    tattoos      = { ZONE_TORSO = { { name, collection, hashMale, hashFemale, zone, label, opacity } } },
    eyeColor     = 0,
}
```

### setAppearance(appearance)

Applies a full appearance table to the player, model change included. This only changes the ped - it does not save to the database.

```lua
exports['meteo-appearance']:setAppearance(appearance)
```

### isWearingGloves()

`true` when the player's arms drawable is one with gloves.

```lua
if exports['meteo-appearance']:isWearingGloves() then
    -- no fingerprints
end
```

### isWearingDuffelbag()

`true` when the player's bag slot holds a duffel bag.

```lua
print(exports['meteo-appearance']:isWearingDuffelbag()) --> false
```

***

## Client: Other Peds

For multicharacter screens and preview peds.

### getAppearanceByCitizenId(citizenid)

The saved appearance of any character, or `nil`.

```lua
local appearance = exports['meteo-appearance']:getAppearanceByCitizenId('ABC12345')
```

### getModelByCitizenId(citizenid)

Just the saved model name, or `nil`. Use it to spawn the right model before dressing the ped.

```lua
local model = exports['meteo-appearance']:getModelByCitizenId('ABC12345')
print(model) --> mp_f_freemode_01
```

### loadAppearanceOnPed(data, ped)

Dresses a ped you created. `data` is a citizenid or an appearance table. The ped must already have the right model.

```lua
local ok = exports['meteo-appearance']:loadAppearanceOnPed('ABC12345', previewPed)
print(ok) --> true
--> false if the ped does not exist or no appearance was found
```

### applyInitialClothesToPed(ped, gender)

Puts the default new character clothes from `Config.initialPlayerClothes` on a freemode ped. `gender` is `'male'`, `'female'`, `0` or `1`.

```lua
local ok = exports['meteo-appearance']:applyInitialClothesToPed(previewPed, 'male')
```

Returns `false` if the ped does not exist.

***

## Client: Low Level

Read and write single parts of a ped. Every one takes the ped handle first. These only change the ped - nothing is saved.

### Getters

| Export | Returns |
| ------ | ------- |
| `getPedAppearance(ped)` | The full appearance table shown above |
| `getPedModel(ped)` | Model name, e.g. `mp_m_freemode_01` |
| `getPedComponents(ped)` | `{ { component_id, drawable, texture } }` |
| `getPedProps(ped)` | `{ { prop_id, drawable, texture } }` |
| `getPedHeadBlend(ped)` | `{ shapeFirst, shapeSecond, shapeThird, skinFirst, skinSecond, skinThird, shapeMix, skinMix, thirdMix }` |
| `getPedFaceFeatures(ped)` | `{ [feature] = value }` |
| `getPedHeadOverlays(ped)` | `{ [overlay] = { style, opacity, color, secondColor } }` |
| `getPedHair(ped)` | `{ style, color, highlight, texture, fade }` |
| `getPedTattoos()` | The player's tattoos by zone. Takes no ped |

```lua
local hair = exports['meteo-appearance']:getPedHair(PlayerPedId())
print(hair.style, hair.color) --> 4  0
```

### Setters

| Export | Notes |
| ------ | ----- |
| `setPlayerModel(model)` | Model name or hash. Clears tattoos. Returns the new ped |
| `setPlayerAppearance(appearance)` | Model change plus everything else |
| `setPedAppearance(ped, appearance)` | Everything except the model |
| `setPedComponent(ped, component)` | `{ component_id, drawable, texture }`. Face and hair are skipped on freemode peds |
| `setPedComponents(ped, components)` | List of the above |
| `setPedProp(ped, prop)` | `{ prop_id, drawable, texture }`. `drawable = -1` removes the prop |
| `setPedProps(ped, props)` | List of the above |
| `setPedHeadBlend(ped, headBlend)` | Freemode peds only |
| `setPedFaceFeatures(ped, faceFeatures)` | |
| `setPedHeadOverlays(ped, headOverlays)` | |
| `setPedHair(ped, hair, tattoos?)` | |
| `setPedEyeColor(ped, eyeColor)` | |
| `setPedTattoos(ped, tattoos)` | Replaces every tattoo |
| `addPedTattoo(ped, tattoo)` | `{ name, collection, hashMale, hashFemale, zone, label?, opacity? }` |
| `removePedTattoo(ped, tattoo)` | Needs `zone` and `name` |
| `clearPedTattooZone(ped, zone)` | e.g. `'ZONE_TORSO'` |

```lua
local ped = PlayerPedId()
exports['meteo-appearance']:setPedComponent(ped, { component_id = 11, drawable = 15, texture = 0 })
exports['meteo-appearance']:setPedProp(ped, { prop_id = 0, drawable = -1, texture = 0 }) -- hat off
```

***

## Server: Custom Peds

Give a character a non-freemode ped, like a staff or event ped. Their freemode look is backed up and comes back with `RestoreCustomPed`. If the player is online, the change is applied live and they get a notification.

### SetCustomPed(citizenid, model)

```lua
local ok, err = exports['meteo-appearance']:SetCustomPed('ABC12345', 'a_c_chimp')
print(ok, err) --> true  nil
```

Errors: `not_found`, `bad_model`, `freemode_model`, and when the player is online `busy` (dead, loading or in the menu) or `dead`.

### RestoreCustomPed(citizenid)

Puts the backed up freemode look back.

```lua
local ok, err = exports['meteo-appearance']:RestoreCustomPed('ABC12345')
```

Errors: `not_found`, `no_custom_ped`, `bad_model`, `busy`, `dead`.

### GetCustomPed(citizenid)

The custom ped model, or `nil` if they do not have one.

```lua
print(exports['meteo-appearance']:GetCustomPed('ABC12345')) --> a_c_chimp
```

***

## Compatibility

Scripts written for other clothing resources keep working without edits.

**illenium-appearance exports (client)** - `exports['illenium-appearance']:...` is answered by meteo-appearance for: `getPedAppearance`, `getPedModel`, `getPedComponents`, `getPedProps`, `getPedHeadBlend`, `getPedFaceFeatures`, `getPedHeadOverlays`, `getPedHair`, `getPedTattoos`, `setPlayerModel`, `setPlayerAppearance`, `setPedAppearance`, `setPedComponent`, `setPedComponents`, `setPedProp`, `setPedProps`, `setPedHeadBlend`, `setPedFaceFeatures`, `setPedHeadOverlays`, `setPedHair`, `setPedEyeColor`, `setPedTattoos`, `addPedTattoo`, `removePedTattoo`. The `ped` argument is optional and defaults to the player.

**illenium-appearance events (client)** - `illenium-appearance:client:openClothingShop`, `openBarberShop`, `openTattooShop`, `openSurgeonShop`, `openOutfitMenu`, `loadJobOutfit`, `reloadSkin`.

**qb-clothing events (client)** - `qb-clothing:client:openMenu`, `qb-clothing:client:openOutfitMenu`, `qb-clothing:client:loadPlayerClothing` and `qb-clothes:client:CreateFirstCharacter`.

{% hint style="info" %}
meteo-appearance does not `provide` illenium-appearance in its fxmanifest, so `GetResourceState('illenium-appearance')` still returns `missing`. Scripts that check the resource state before calling the export need `meteo-appearance` added to their check.
{% endhint %}
