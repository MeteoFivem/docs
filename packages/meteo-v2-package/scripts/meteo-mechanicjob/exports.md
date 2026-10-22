---
description: >-
  The meteo-mechanicjob export with a simple example - count on-duty mechanics.
icon: code
---

# Exports

Check how many mechanics are working before your own script lets players repair or tune on their own. meteo-bennys uses this to only offer **Place Order** when a shop has mechanics working.

***

## Server

### GetMechanicOnlineCount(shopJob?)

The number of on-duty players whose job is a mechanic shop job.

```lua
local all = exports['meteo-mechanicjob']:GetMechanicOnlineCount()
local tuners = exports['meteo-mechanicjob']:GetMechanicOnlineCount('tunershop')

print(all, tuners) --> 3  1

if all > 0 then
    return QBCore.Functions.Notify(source, 'A mechanic is on duty, go see them', 'error')
end
```

| Parameter | Type | Notes |
| --------- | ---- | ----- |
| `shopJob` | string | Optional. A shop's job name to count only that shop. Leave it out to count every shop |

Returns a number. Off-duty mechanics are not counted.
