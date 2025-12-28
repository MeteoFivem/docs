# Laber App - Custom Jobs

Simple guide about how to add your custom jobs to meteo phone built in laber app without meteo job resources.

### Method 1: Config (Static)

In `shared/config.lua`:

```lua
laber = {
    enabled = true,
    jobs = { ... }, -- meteo resource-based jobs
    customJobs = {
        {
            id = 'mining',
            name = 'Miner',
            icon = 'hardware',  -- Material icon name
            location = vector3(2950.0, 2780.0, 40.0),
            blip = {
                sprite = 618,
                color = 1,
                scale = 0.7
            }
        },
        {
            id = 'fishing',
            name = 'Fisherman',
            icon = 'phishing',
            location = vector3(-1850.0, -1250.0, 8.0),
            blip = {
                sprite = 317,
                color = 3,
                scale = 0.8
            }
        }
    }
}
```

### Method 2: Exports (Dynamic)

**IMPORTANT: These exports are SERVER-SIDE only.**

#### Register a Custom Job

```lua
-- server-side
exports['meteo-phone']:RegisterCustomLaberJob({
    id = 'mining',
    name = 'Miner',
    icon = 'hardware',
    location = vector3(2950.0, 2780.0, 40.0),
    blip = { sprite = 618, color = 1, scale = 0.7 }
})
```

#### Get All Custom Jobs

```lua
-- server-side
local customJobs = exports['meteo-phone']:GetCustomLaberJobs()
```

### Job Data Structure

<table><thead><tr><th width="88.5">Field</th><th width="101">Type</th><th width="130">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Yes</td><td>Unique identifier</td></tr><tr><td>name</td><td>string</td><td>Yes</td><td>Display name in UI</td></tr><tr><td>icon</td><td>string</td><td>No</td><td>Material icon name (default: 'work')</td></tr><tr><td>location</td><td>vector3</td><td>No</td><td>Waypoint coordinates</td></tr><tr><td>blip</td><td>table</td><td>No</td><td>Blip settings { sprite, color, scale }</td></tr></tbody></table>

