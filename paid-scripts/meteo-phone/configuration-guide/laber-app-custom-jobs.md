# Laber App - Custom Jobs

Simple guide about how to add your custom jobs to meteo phone built in laber app without meteo job resources.

### Method 1: Config (Static)

In `shared/config.lua`:

```lua
laber = {
    enabled = true,
    jobs = { ... }, -- resource-based jobs
    customJobs = {
        -- Single blip example
        {
            id = 'mining',
            name = 'Miner',
            icon = 'hardware',  -- Material icon name
            location = vector3(2950.0, 2780.0, 40.0),  -- Waypoint location
            blips = {
                { location = vector3(2950.0, 2780.0, 40.0), name = 'Mine Entrance', sprite = 618, color = 1, scale = 0.7 }
            }
        },
        -- Multiple blips with custom names
        {
            id = 'hunting',
            name = 'Hunter',
            icon = 'pets',
            location = vector3(-773.26, 5597.76, 33.61), -- Waypoint location
            blips = {
                { location = vector3(-773.26, 5597.76, 33.61), name = 'Hunting Store', sprite = 141, color = 1, scale = 0.7 },
                { location = vector3(-42.38, -1473.82, 31.81), name = 'Hunting Sell', sprite = 141, color = 3, scale = 0.7 }
            }
        }
    }
}
```

### Method 2: Exports (Dynamic)

**IMPORTANT: These exports are SERVER-SIDE only.**

#### Register a Custom Job (Single Blip)

```lua
-- server-side
exports['meteo-phone']:RegisterCustomLaberJob({
    id = 'mining',
    name = 'Miner',
    icon = 'hardware',
    location = vector3(-773.26, 5597.76, 33.61), -- Waypoint location
    blips = {
        { location = vector3(-773.26, 5597.76, 33.61), name = 'Hunting Store', sprite = 141, color = 1, scale = 0.7 },
    }
})
```

#### Register a Custom Job (Multiple Blips)

```lua
-- server-side
exports['meteo-phone']:RegisterCustomLaberJob({
    id = 'hunting',
    name = 'Hunter',
    icon = 'pets',
    location = vector3(-773.26, 5597.76, 33.61), -- Waypoint location
    blips = {
        { location = vector3(-773.26, 5597.76, 33.61), name = 'Hunting Store', sprite = 141, color = 1, scale = 0.7 },
        { location = vector3(-42.38, -1473.82, 31.81), name = 'Hunting Sell', sprite = 141, color = 3, scale = 0.7 }
    }
})
```

#### Get All Custom Jobs

```lua
-- server-side
local customJobs = exports['meteo-phone']:GetCustomLaberJobs()
```



### Job Data Structure

| Field    | Type     | Required | Description                                       |
| -------- | -------- | -------- | ------------------------------------------------- |
| id       | string   | Yes      | Unique identifier                                 |
| name     | string   | Yes      | Display name in UI                                |
| icon     | string   | No       | Material icon name (default: 'work')              |
| location | vector3  | No       | Waypoint coordinates (for "Mark Location" button) |
| blips    | table\[] | No       | Array of blip objects (see below)                 |
