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

<table><thead><tr><th width="107.5">Field</th><th width="89.5">Type</th><th width="83.5">Required</th><th>Description</th></tr></thead><tbody><tr><td>id</td><td>string</td><td>Yes</td><td>Unique identifier</td></tr><tr><td>name</td><td>string</td><td>Yes</td><td>Display name in UI</td></tr><tr><td>icon</td><td>string</td><td>No</td><td>Material icon name (default: 'work')</td></tr><tr><td>location</td><td>vector3</td><td>No</td><td>Waypoint coordinates</td></tr><tr><td>blip</td><td>table</td><td>No</td><td>Blip settings { sprite, color, scale }</td></tr></tbody></table>
{% endstep %}
{% endstepper %}

