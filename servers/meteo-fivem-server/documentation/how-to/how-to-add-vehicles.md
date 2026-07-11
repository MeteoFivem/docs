---
description: >-
  How to add new vehicles to your meteo fivem server. Add to qbx_core shared
  vehicles, check dealership config and import via admin panel.
icon: car
---

# How to Add Vehicles

Quick guide for adding new vehicles to your server.

***

## Step by Step

{% stepper %}
{% step %}
**Add vehicle to qbx\_core**

Open `qbx_core/shared/vehicles.lua` and add your vehicle. Each entry is keyed by its spawn name:

```lua
meteoc17 = {
    name = 'Dominator GT CTX C3',
    brand = 'Vapid',
    model = 'meteoc17',
    price = 80000,
    category = 'custom',
    type = 'automobile',
    shop = 'pdm',
    customclass = 'C',
    hash = `meteoc17`,
},
```

| Field | What it is |
| ----- | ---------- |
| `name` | Display name in shop |
| `brand` | Manufacturer |
| `model` | Spawn name (GTA model) |
| `price` | Base price |
| `category` | Vehicle category |
| `type` | `automobile`, `bike`, `boat`, `plane`, `heli` |
| `shop` | Which shop sells it (string or array) |
| `customclass` | Optional - force a class (S, A, B, C, D, E) |
| `hash` | Model hash - wrap the spawn name in backticks, e.g. `` `meteoc17` `` |
{% endstep %}

{% step %}
**Check dealership config**

In `meteo-dealerships/shared/config.lua`, make sure the dealership has your vehicle's **category** in `categories` and your vehicle's **shop** in `shops`:

```lua
pdm = {
    categories = { 'custom', 'sports', 'super' },  -- 'custom' is here
    shops = { 'pdm' },                              -- 'pdm' is here
}
```
{% endstep %}

{% step %}
**Import via admin panel**

Run `/dealeradmin` in game, select your dealership and click "Import Vehicles". Your new vehicle will appear in the catalog and is ready to sell.
{% endstep %}
{% endstepper %}

***

{% hint style="info" %}
For more advanced vehicle setup like custom images, class rules and finance settings check out the [Meteo Dealerships developer guide](../../../paid-scripts/meteo-dealerships/for-developers/adding-new-vehicles.md).
{% endhint %}
