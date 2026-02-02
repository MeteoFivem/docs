---
description: >-
  Add a new apartment MLO to your server. Works with any apartment building.
---

# Adding New Complex

This guide shows you how to set up a new apartment MLO (building) for use with Meteo Apartments.

***

## What You Need

- Your apartment MLO installed and working
- Coordinates for elevator locations
- Coordinates for NPC location (optional)
- Coordinates for garage (optional)

***

## Step-by-Step Setup

{% stepper %}
{% step %}
### Copy the Template

1. Go to `meteo-apartments/shared/complexes/`
2. Copy `TEMPLATE.txt`
3. Rename it to your complex name (e.g., `my_apartments.lua`)

{% hint style="warning" %}
**File must be .lua extension**, not .txt. Make sure to rename it properly.
{% endhint %}
{% endstep %}

{% step %}
### Configure Basic Info

Open your new file and fill in the basic details:

```lua
return {
    label = 'My Apartment Complex',  -- Display name
    coords = vec3(100.0, 200.0, 30.0),  -- Complex center coords
    startingRoom = 1,  -- First room number
    totalRooms = 20,  -- How many rooms you want
    roomType = 'modern',  -- Room type (affects price)
    startingEnabled = true,  -- Show in spawn selection?
```

**Room types available:**
- `modern` - $25,000
- `classic` - $15,000
- `luxury` - $50,000
- `penthouse` - $100,000

You can change prices in `shared/config.lua`
{% endstep %}

{% step %}
### Add Elevator Locations

Most MLO creators include elevator coordinates. Check your MLO files or documentation for elevator locations.

**Remove the template defaults and add your elevator coords:**

```lua
elevator = {
    { coords = vec4(100.0, 200.0, 30.0, 0.0), label = 'Lobby' },
    { coords = vec4(100.0, 200.0, 35.0, 0.0), label = 'Floor 1' },
    { coords = vec4(100.0, 200.0, 40.0, 0.0), label = 'Floor 2' },
},
```

**How to get elevator coords:**
1. Check your MLO files (usually in a .lua file included with the MLO)
2. Check MLO creator's documentation or forum post
3. Or stand at elevator location and use a coords script to get vec4

{% hint style="warning" %}
**Remove the template coordinates.** Don't leave the default `vec4(0.0, 0.0, 0.0, 0.0)` - replace with your actual elevator locations.
{% endhint %}

{% hint style="danger" %}
**Remove MLO's elevator script.** If your MLO includes its own elevator script, delete it and remove it from the fxmanifest.lua. Having both elevator systems will cause conflicts.
{% endhint %}

{% hint style="info" %}
**Elevators are required.** Even if you only have one floor, add at least one elevator location.
{% endhint %}
{% endstep %}

{% step %}
### Configure Blip (Optional)

Add a map blip for your complex:

```lua
blip = {
    enabled = true,
    sprite = 475,  -- Blip icon (475 = apartment icon)
    color = 2,  -- Color (2 = green)
    scale = 0.7  -- Size
},
```

**Leave disabled if you don't want a blip:**
```lua
blip = {
    enabled = false
},
```
{% endstep %}

{% step %}
### Configure NPC (Optional)

Add an NPC for apartment browsing:

```lua
npc = {
    enabled = true,
    coords = vec4(100.0, 200.0, 30.0, 180.0),  -- NPC location and heading
    model = 'a_f_y_business_01',  -- Ped model
    scenario = 'WORLD_HUMAN_CLIPBOARD'  -- Animation
},
```

**Leave disabled if you don't want an NPC:**
```lua
npc = {
    enabled = false
},
```
{% endstep %}

{% step %}
### Configure Garage (Optional)

Add a garage for vehicle storage:

```lua
garage = {
    id = 'my_complex_garage',  -- Unique garage ID
    vehicleClass = nil,  -- nil = cars, 'boat' = boats, 'air' = aircraft
    spawnPoint = vec4(100.0, 200.0, 30.0, 0.0),  -- Where vehicles spawn
    ped = {
        coords = vec4(100.0, 200.0, 30.0, 180.0),  -- Garage NPC
        model = 's_m_y_valet_01',
        scenario = 'WORLD_HUMAN_CLIPBOARD'
    },
    parkZone = {
        coords = vec3(100.0, 200.0, 30.0),
        radius = 5.0  -- How close to park
    }
},
```

**Leave nil if no garage:**
```lua
garage = nil,
```
{% endstep %}

{% step %}
### Register the Complex

Open `meteo-apartments/shared/main.lua` and add your complex:

```lua
Apartments.Complexes = {
    wiwang_hotel = require 'shared.complexes.wiwang_hotel',
    my_apartments = require 'shared.complexes.my_apartments',  -- Add this line
}
```

{% hint style="success" %}
**That's it for the complex setup!** Now you need to create rooms using the in-game creator.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## What's Next?

Your complex is configured, but it has no rooms yet. The `rooms = {}` table is empty.

**Next step:** [**Creating Rooms**](creating-rooms.md) - Use the in-game creator to add rooms to your complex.

***

## Example Configuration

Here's a complete example for reference:

```lua
return {
    label = 'Downtown Apartments',
    coords = vec3(-624.73, -702.12, 28.06),
    startingRoom = 1,
    totalRooms = 15,
    roomType = 'modern',
    startingEnabled = true,

    blip = {
        enabled = true,
        sprite = 475,
        color = 2,
        scale = 0.7
    },

    npc = {
        enabled = true,
        coords = vec4(-624.73, -702.12, 28.06, 180.0),
        model = 'a_f_y_business_01',
        scenario = 'WORLD_HUMAN_CLIPBOARD'
    },

    elevator = {
        { coords = vec4(-624.73, -702.12, 28.06, 0.0), label = 'Lobby' },
        { coords = vec4(-624.73, -702.12, 33.06, 0.0), label = 'Floor 1' },
    },

    rooms = {
        -- Will be filled by the creator tool
    }
}
```

***

## Troubleshooting

### Complex not showing in-game?

Make sure you:
1. Saved the .lua file (not .txt)
2. Registered it in `shared/main.lua`
3. Restarted the resource

### Elevator menu not opening?

Check that elevator coords are correct. Stand at the location and use `/aptdev` → "Get Coords" to verify.

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
