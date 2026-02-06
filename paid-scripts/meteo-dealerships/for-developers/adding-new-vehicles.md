---
description: How to add vehicles to your dealerships.
---

# Adding New Vehicles

## How do vehicles show up at a dealership?

For a vehicle to appear at a dealership, **two things must match**:

| Check          | Vehicle Field         | Dealership Config                |
| -------------- | --------------------- | -------------------------------- |
| Category match | `category = 'sports'` | `categories = { 'sports', ... }` |
| Shop match     | `shop = 'pdm'`        | `shops = { 'pdm', ... }`         |

Both must match. If category matches but shop doesn't - vehicle won't show.

{% hint style="info" %}
If a dealership's `shops` is empty (`shops = {}`), the shop filter is skipped - it will show **all vehicles matching its categories** regardless of shop assignment.
{% endhint %}

***

## Easy Way: Admin Panel

Don't want to edit config files? Use the admin panel:

1. Run `/dealeradmin`
2. Go to vehicle catalog
3. Click edit on any vehicle
4. Check/uncheck shop boxes to assign dealerships
5. Add custom shop names if needed

{% hint style="info" %}
Shop names matching dealership IDs (like `pdm`, `boats`, `lsa`) are highlighted so you know which dealership gets the vehicle.
{% endhint %}

***

## Adding Vehicles via Config

### QBCore Format

QBCore uses an **array** format in `qb-core/shared/vehicles.lua`:

```lua
{ model = 'sultan', name = 'Sultan', brand = 'Karin', price = 45000, category = 'sports', type = 'automobile', shop = 'pdm' },
```

### QBox Format

QBox uses a **keyed table** format in `shared/vehicles.lua`. Note that QBox vehicles **don't have a `shop` field** by default:

```lua
sultan = {
    name = 'Sultan',
    brand = 'Karin',
    model = 'sultan',
    price = 45000,
    category = 'sports',
    type = 'automobile',
    hash = `sultan`,
},
```

{% hint style="warning" %}
QBox vehicles have no `shop` field. After importing, use the **admin panel** to assign shops to vehicles - or set your dealership's `shops = {}` to skip shop filtering and show all vehicles by category only.
{% endhint %}

### Quick Example

```lua
-- QBCore shared/vehicles.lua
{ model = 'sultan', name = 'Sultan', brand = 'Karin', price = 45000, category = 'sports', type = 'automobile', shop = 'pdm' },

-- meteo-dealerships config.lua
pdm = {
    categories = { 'sports', 'super', 'muscle' },  -- 'sports' ✓
    shops = { 'pdm', 'luxury' },                    -- 'pdm' ✓
}
-- Result: Sultan shows at PDM
```

***

## Step by Step

{% stepper %}
{% step %}
#### Add Vehicle to QBCore / QBox

**QBCore** - open `qb-core/shared/vehicles.lua`:

```lua
{ model = 'meteoc17', name = 'Dominator GT CTX C3', brand = 'Vapid', price = 80000, category = 'custom', type = 'automobile', shop = 'pdm', customclass = 'C' },
```

**QBox** - open `shared/vehicles.lua`. QBox doesn't have `shop` by default, but you can just add it:

```lua
meteoc17 = {
    name = 'Dominator GT CTX C3',
    brand = 'Vapid',
    model = 'meteoc17',
    price = 80000,
    category = 'custom',
    type = 'automobile',
    hash = `meteoc17`,
    shop = 'pdm',  -- just add this field
},
```

{% hint style="info" %}
If you don't want to add `shop` to every QBox vehicle, set your dealership's `shops = {}` in the config. This skips shop filtering and shows all vehicles by category only. Or assign shops via the admin panel after importing.
{% endhint %}

| Field         | What it is                                    |
| ------------- | --------------------------------------------- |
| `model`       | Spawn name (GTA model)                        |
| `name`        | Display name in shop                          |
| `brand`       | Manufacturer                                  |
| `price`       | Base price                                    |
| `category`    | Vehicle category                              |
| `type`        | `automobile`, `bike`, `boat`, `plane`, `heli` |
| `shop`        | Which shop sells it (string or array)         |
| `customclass` | Optional - force a class (S, A, B, C, D, E)   |
{% endstep %}

{% step %}
#### Check Dealership Config

In `meteo-dealerships/shared/config.lua`, make sure the dealership has:

* Vehicle's **category** in `categories`
* Vehicle's **shop** in `shops`

```lua
pdm = {
    categories = { 'custom', 'sports', 'super' },  -- 'custom' is here
    shops = { 'pdm' },                              -- 'pdm' is here
}
```
{% endstep %}

{% step %}
#### Import via Admin Panel

1. Run `/dealeradmin` in game
2. Select your dealership
3. Click "Import Vehicles"
4. Your new vehicle appears in the catalog
{% endstep %}
{% endstepper %}

***

## Multiple Dealerships

Want a vehicle at multiple dealerships? Use an array for `shop`:

```lua
{ model = 'zentorno', name = 'Zentorno', brand = 'Pegassi', price = 2100000, category = 'super', type = 'automobile', shop = { 'pdm', 'luxury' } },
```

Now it shows at any dealership that has `'pdm'` OR `'luxury'` in their `shops` config.

***

## Custom Shop Names

You can use any shop name. Just make sure both sides match:

```lua
-- QBCore vehicle
{ model = 'luxor', name = 'Luxor', brand = 'Buckingham', price = 1625000, category = 'planes', type = 'plane', shop = 'air' },

-- Dealership config
lsa = {
    categories = { 'planes', 'helicopters' },
    shops = { 'air' },  -- matches 'air' in vehicle
}
```

***

## Common Examples

### Standard Car

```lua
{ model = 'sultan', name = 'Sultan', brand = 'Karin', price = 45000, category = 'sports', type = 'automobile', shop = 'pdm' },
```

### Custom Add-On with Class Override

```lua
{ model = 'meteoc17', name = 'Dominator GT CTX C3', brand = 'Vapid', price = 80000, category = 'custom', type = 'automobile', shop = 'pdm', customclass = 'C' },
```

### Boat

```lua
{ model = 'speeder', name = 'Speeder', brand = 'Pegassi', price = 325000, category = 'boats', type = 'boat', shop = 'boats' },
```

### Helicopter

```lua
{ model = 'buzzard', name = 'Buzzard', brand = 'Nagasaki', price = 1750000, category = 'helicopters', type = 'heli', shop = 'air' },
```

### Multi-Shop Vehicle

```lua
{ model = 'adder', name = 'Adder', brand = 'Truffade', price = 1000000, category = 'super', type = 'automobile', shop = { 'pdm', 'luxury' } },
```

***

## Troubleshooting

| Problem              | Fix                                                      |
| -------------------- | -------------------------------------------------------- |
| Vehicle not showing  | Check both `category` AND `shop` match dealership config |
| Not imported yet     | Use admin panel "Import Vehicles" button                 |
| Shop shows as "None" | Edit vehicle in admin panel and assign a shop            |
| Changed config       | Restart the resource                                     |

***

## Need Help?

* Discord: [discord.meteofivem.net](http://discord.meteofivem.net/)
