---
description: >-
  Step-by-step guide for adding new dealerships to your server. Covers all
  configuration options, multiple locations, and QBCore vehicle setup.
---

# Adding a New Dealership

## How do I add a new dealership?

Open `shared/config.lua` and add a new entry to `Config.dealerships`. Each dealership needs a unique ID.

```lua
Config.dealerships = {
    -- Your existing dealerships...

    -- Add your new dealership
    boats = {
        name = 'Marina Yacht Club',
        mode = 'public',
        categories = { 'boats' },
        shops = { 'boats' },
        -- ... rest of config
    }
}
```

After adding, restart the resource. New dealerships appear in the admin panel automatically.

***

## What's the difference between owned and public?

| Mode | Description | Use Case |
|------|-------------|----------|
| `owned` | Employee-managed with inventory, banking, sales tracking | Player-run businesses |
| `public` | Self-service, always open, unlimited stock | Government/NPC dealerships |

**Owned dealerships** require an owner (set via admin panel) and employees to operate. They track inventory, sales, and have banking features.

**Public dealerships** work like traditional FiveM dealerships - anyone can buy vehicles directly.

***

## Complete Configuration Reference

### Basic Settings

```lua
mydealer = {
    name = 'My Dealership',
    mode = 'owned',                            -- 'owned' or 'public'
    categories = { 'sports', 'super' },        -- GTA vehicle categories
    shops = { 'pdm', 'luxury' },               -- QBCore shop names to accept
}
```

**categories** - must match QBCore vehicle categories:

| Category | Description |
|----------|-------------|
| `compacts` | Small cars |
| `sedans` | Family sedans |
| `suvs` | SUVs and crossovers |
| `coupes` | Two-door coupes |
| `muscle` | Muscle cars |
| `sports` | Sports cars |
| `sportsclassics` | Classic sports cars |
| `super` | Supercars |
| `motorcycles` | Bikes |
| `offroad` | Off-road vehicles |
| `industrial` | Industrial vehicles |
| `utility` | Utility vehicles |
| `vans` | Vans |
| `boats` | Boats |
| `helicopters` | Helicopters |
| `planes` | Planes |
| `commercial` | Commercial vehicles |
| `openwheel` | Open wheel racers |
| `custom` | Custom add-on vehicles |

```lua
-- Example: dealership accepts vehicles with shop = 'pdm' or shop = 'luxury'
shops = { 'pdm', 'luxury' }
```

{% hint style="info" %}
A vehicle appears at a dealership only if **both** its category AND shop match. See [Adding New Vehicles](adding-new-vehicles.md) for details.
{% endhint %}

***

### Map Blip

```lua
blip = {
    show = true,    -- Show on map
    icon = 326,     -- Blip sprite ID (326 = car dealership)
    color = 2,      -- Blip color ID (2 = green)
    size = 0.7      -- Blip scale
}
```

{% hint style="info" %}
Find blip sprites and colors at [docs.fivem.net/docs/game-references/blips](https://docs.fivem.net/docs/game-references/blips/)
{% endhint %}

***

### Shop Locations (Multiple Supported)

The `shop` table defines where customers browse vehicles. You can have multiple browse locations for large dealerships.

```lua
-- Single location
shop = {
    { coords = vec4(-57.20, -1097.33, 26.42, 203.58), preview = vec4(-44.32, -1094.54, 26.01, 130.42) }
}

-- Multiple locations (large dealership with indoor + outdoor areas)
shop = {
    { coords = vec4(-57.20, -1097.33, 26.42, 203.58), preview = vec4(-44.32, -1094.54, 26.01, 130.42) },
    { coords = vec4(-45.50, -1082.00, 26.42, 180.00), preview = vec4(-50.00, -1085.00, 26.01, 90.00) },
    { coords = vec4(-30.00, -1095.00, 26.42, 270.00), preview = vec4(-35.00, -1090.00, 26.01, 45.00) }
}

-- With custom camera for boats/aircraft (optional)
shop = {
    {
        coords = vec4(-729.55, -1319.56, 1.60, 122.61),
        preview = vec4(-713.36, -1335.06, 0.09, 204.21),
        camera = {
            distance = 10.0,    -- Further back for large vehicles
            height = 3.0,       -- Higher angle
            angle = 45,
            fov = 50.0,
            pointHeight = 1.0
        }
    }
}
```

| Property | Description |
|----------|-------------|
| `coords` | Where the target interaction appears (vec4 with heading) |
| `preview` | Where the preview vehicle spawns when browsing (vec4 with heading) |
| `camera` | Optional per-location camera settings (falls back to Config.camera) |

#### Camera Settings

| Setting | Description | Default |
|---------|-------------|---------|
| `distance` | How far camera is from vehicle | 6.0 |
| `height` | Camera height above vehicle | 1.0 |
| `angle` | Angle offset from vehicle heading | 50 |
| `fov` | Field of view | 50.0 |
| `pointHeight` | Where camera looks at (height offset) | 0.3 |

{% hint style="info" %}
Custom camera is useful for boats and aircraft where the default car camera doesn't work well.
{% endhint %}

***

### Manage Location (Owned Only)

Where employees access inventory, sales, banking, and management features.

```lua
manage = vec4(-30.76, -1106.69, 26.42, 333.09)
```

Only visible to employees and owners.

***

### Sellback Location

Where customers sell vehicles back to the dealership.

```lua
sellback = vec4(-46.16, -1082.50, 26.33, 247.29)
```

Player must be in a vehicle to use this. Shows a marker and keybind when in range.

***

### Finance NPC

Handles finance payments and repossessed vehicle recovery.

```lua
finance = {
    coords = vec4(-33.25, -1103.91, 26.42, 68.66),  -- NPC location
    model = 's_m_m_autoshop_01',                     -- Ped model
    anim = 'WORLD_HUMAN_CLIPBOARD',                  -- Scenario animation
    recoverySpawn = vec4(-14.53, -1106.84, 26.42, 160.0)  -- Where recovered vehicles spawn
}
```

***

### Vehicle Spawn Points

Where purchased and test drive vehicles spawn.

```lua
spawn = {
    points = {
        vec4(-45.32, -1115.84, 26.02, 1.93),
        vec4(-47.93, -1115.92, 26.02, 3.67),
        vec4(-50.74, -1115.88, 26.02, 4.80),
    },
    warpPlayer = false  -- true = teleport into car, false = spawn car only
}
```

Multiple spawn points prevent vehicles from spawning on top of each other.

***

### Test Drive Settings

```lua
testdrive = {
    enabled = true,
    publicAccess = false,   -- false = employees only, true = anyone
    minutes = 5,            -- Duration in minutes
    returnPoint = vec4(-58.39, -1108.80, 26.02, 76.38),  -- Return location
    teleportBack = false    -- true = teleport player back when time runs out
}
```

***

### Showroom Display Vehicles

Static display vehicles in the dealership. Owners can change these via the manage menu.

```lua
showroom = {
    { coords = vec4(-36.33, -1101.42, 26.01, 159.55), model = 'adder' },
    { coords = vec4(-46.15, -1102.13, 26.01, 65.41), model = 't20' },
    { coords = vec4(-51.25, -1096.00, 26.01, 26.18), model = 'zentorno' }
}
```

Leave empty for no display vehicles:

```lua
showroom = {}
```

***

### Shops Config

The `shops` field defines which QBCore/QBox shop names this dealership accepts:

```lua
-- Accept vehicles with shop = 'pdm' or shop = 'luxury'
shops = { 'pdm', 'luxury' }

-- Accept only boats shop
shops = { 'boats' }

-- Empty = skip shop filter, show ALL vehicles matching categories
shops = {}
```

This must match the `shop` field in your vehicle config. You can also edit shop assignments in the admin panel.

{% hint style="info" %}
**QBox users:** QBox vehicles don't have a `shop` field by default. You can either add `shop = 'pdm'` to your QBox vehicle entries, assign shops via the admin panel, or just use `shops = {}` to skip shop filtering entirely.
{% endhint %}

***

## How do I add vehicles?

Vehicles must exist in your framework's shared vehicles. See [Adding New Vehicles](adding-new-vehicles.md) for the full guide.

### QBCore Examples

```lua
-- qb-core/shared/vehicles.lua
{ model = 'sultan', name = 'Sultan', brand = 'Karin', price = 45000, category = 'sports', type = 'automobile', shop = 'pdm' },
{ model = 'zentorno', name = 'Zentorno', brand = 'Pegassi', price = 2100000, category = 'super', type = 'automobile', shop = { 'pdm', 'luxury' } },
{ model = 'speeder', name = 'Speeder', brand = 'Pegassi', price = 325000, category = 'boats', type = 'boat', shop = 'boats' },
```

### QBox Examples

```lua
-- shared/vehicles.lua (just add shop field)
sultan = {
    name = 'Sultan', brand = 'Karin', model = 'sultan',
    price = 45000, category = 'sports', type = 'automobile',
    hash = `sultan`, shop = 'pdm',
},
```

***

## Full Dealership Example

Here's a complete boat dealership configuration with custom camera:

```lua
boats = {
    name = 'Los Santos Marina',
    mode = 'owned',

    categories = { 'boats' },
    shops = { 'boats' },

    blip = {
        show = true,
        icon = 410,     -- Boat icon
        color = 3,      -- Blue
        size = 0.8
    },

    shop = {
        {
            coords = vec4(-729.55, -1319.56, 1.60, 122.61),
            preview = vec4(-713.36, -1335.06, 0.09, 204.21),
            camera = {
                distance = 10.0,    -- Further back for boats
                height = 3.0,       -- Higher angle
                angle = 45,
                fov = 50.0,
                pointHeight = 1.0
            }
        }
    },

    manage = vec4(-725.00, -1315.00, 1.60, 90.00),

    sellback = vec4(-735.00, -1325.00, 1.60, 180.00),

    finance = {
        coords = vec4(-720.00, -1312.00, 1.60, 90.00),
        model = 's_m_y_dockwork_01',
        anim = 'WORLD_HUMAN_CLIPBOARD',
        recoverySpawn = vec4(-740.00, -1340.00, 0.00, 180.00)
    },

    spawn = {
        points = {
            vec4(-740.00, -1340.00, 0.00, 180.00),
            vec4(-745.00, -1345.00, 0.00, 180.00),
        },
        warpPlayer = true
    },

    testdrive = {
        enabled = true,
        publicAccess = false,
        minutes = 3,
        returnPoint = vec4(-730.00, -1330.00, 0.00, 150.00),
        teleportBack = true
    },

    showroom = {},
}
```

***

## Common Issues

### Vehicles not showing up

1. Check that vehicle's `category` is in dealership's `categories = {}`
2. Check that vehicle's `shop` is in dealership's `shops = {}`
3. Both must match - not just one
4. Use admin panel to import vehicles after adding the dealership
5. Restart the resource after config changes

### Preview vehicle spawning underground

Adjust the Z coordinate in your `preview` vec4. Water vehicles need negative Z values.

### Target not appearing

Make sure coords have proper heading (4th value in vec4). The target spawns at ground level automatically.

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
