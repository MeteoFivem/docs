---
description: >-
  Every meteo-bossmenu export with a simple example - add entries to a job's
  activity feed, check a job has a boss menu, and open the menu.
icon: code
---

# Exports

Write to a job's activity feed and check a job is set up, from your own scripts. Server exports for the feed, one client export to open the menu.

***

## Server

### AddActivityLog(jobName, data)

Adds an entry to the job's **Activity** feed in the boss menu. Good for invoices, orders, deliveries and payouts your script handles.

```lua
local ok = exports['meteo-bossmenu']:AddActivityLog('mechanic', {
    action        = 'invoice',             -- required, short key
    details       = 'Sent Invoice #4 to John Doe ($450)', -- required, the line shown
    label         = 'Invoice',             -- optional, the tag shown on the entry
    icon          = 'receipt',             -- optional, Material Icons name
    amount        = 450,                   -- optional
    performedBy   = 'CJ Johnson',          -- optional, defaults to 'System'
    performedById = 'ABC12345',            -- optional, citizenid
})
print(ok) --> true
```

| Field | Type | Notes |
| ----- | ---- | ----- |
| `action` | string | Required |
| `details` | string | Required |
| `label` | string | Optional |
| `icon` | string | Optional. A <a href="https://fonts.google.com/icons" target="_blank">Material Icons</a> name, e.g. `receipt`, `build`, `local_shipping`, `payments` |
| `amount` | number | Optional |
| `performedBy` | string | Optional, defaults to `System` |
| `performedById` | string | Optional |

Returns `false` if the job has no boss menu, or `action` or `details` is missing.

### CheckJobConfigured(jobName, callerResource?)

Does this job have a boss menu (and so a society bank)? Prints a warning in the server console naming your resource when it does not.

```lua
CreateThread(function()
    exports['meteo-bossmenu']:CheckJobConfigured('tunershop', GetCurrentResourceName())
end)
```

Returns `true` or `false`. Asked before the admin menu has loaded the boss menus, it returns `true` and checks again (and warns) once they arrive.

***

## Client

### OpenBossMenu()

Opens the boss menu for the player's current job. Players who are not a boss of a job with a boss menu get a "no permission" notification.

```lua
exports['meteo-bossmenu']:OpenBossMenu()
```

***

## Compatibility

* **qbx\_management** - `OpenBossMenu` also answers `exports['qbx_management']:OpenBossMenu(...)`. `AddBossMenuItem`, `AddGangMenuItem`, `RemoveBossMenuItem` and `RemoveGangMenuItem` exist so callers do not error, but do nothing. Gang menus are not supported, so `OpenBossMenu('gang')` does nothing
* **qb-bossmenu / qb-gangmenu** - the `qb-bossmenu:client:OpenMenu` event opens the boss menu. `qb-gangmenu:client:OpenMenu` does nothing
* **Old name** - the server exports also answer `exports['meteo-bossmenuv2']:...`
