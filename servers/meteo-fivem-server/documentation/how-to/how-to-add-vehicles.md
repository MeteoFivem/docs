---
description: >-
  How to add new vehicles to your meteo fivem server. Add to QBCore shared
  vehicles, check dealership config and import via admin panel.
icon: car
---

# How to Add Vehicles

Quick guide for adding new vehicles to your server.

***

## Step by Step

{% stepper %}
{% step %}
**Add vehicle to QBCore**

Open `qb-core/shared/vehicles.lua` and add your vehicle:

```lua
{ model = 'meteoc17', name = 'Dominator GT CTX C3', brand = 'Vapid', price = 80000, category = 'custom', type = 'automobile', shop = 'pdm', customclass = 'C' },
```

| Field | What it is |
| ----- | ---------- |
| `model` | Spawn name (GTA model) |
| `name` | Display name in shop |
| `brand` | Manufacturer |
| `price` | Base price |
| `category` | Vehicle category |
| `type` | `automobile`, `bike`, `boat`, `plane`, `heli` |
| `shop` | Which shop sells it (string or array) |
| `customclass` | Optional - force a class (S, A, B, C, D, E) |
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
