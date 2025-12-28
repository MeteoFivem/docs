# Useful Exports

## Quick Exports Reference Table

| Export                                          | Purpose               | Side             |
| ----------------------------------------------- | --------------------- | ---------------- |
| `exports['meteo-phone']:RegisterCustomLaberJob` | Register a Custom Job | Server side Only |
| `exports['meteo-phone']:GetCustomLaberJobs`     | Get All Custom Jobs   | Server side Only |



{% stepper %}
{% step %}
### RegisterCustomLaberJob

Register a Custom Job

Example

```lua
-- server-side
exports['meteo-phone']:RegisterCustomLaberJob({
    id = 'mining',
    name = 'Miner',
    icon = 'hardware', -- Find icons at: https://fonts.google.com/icons
    location = vector3(2950.0, 2780.0, 40.0),
    blip = { sprite = 618, color = 1, scale = 0.7 }
})
```


{% endstep %}

{% step %}
### GetCustomLaberJobs

Get All Custom Jobs

Example

```lua
-- server-side
local customJobs = exports['meteo-phone']:GetCustomLaberJobs()
```

### Job Data Structure

| Field    | Type    | Required | Description                            |
| -------- | ------- | -------- | -------------------------------------- |
| id       | string  | Yes      | Unique identifier                      |
| name     | string  | Yes      | Display name in UI                     |
| icon     | string  | No       | Material icon name (default: 'work')   |
| location | vector3 | No       | Waypoint coordinates                   |
| blip     | table   | No       | Blip settings { sprite, color, scale } |


{% endstep %}

{% step %}





{% endstep %}
{% endstepper %}

