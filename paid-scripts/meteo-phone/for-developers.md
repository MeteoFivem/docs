---
description: >-
  Everything you need to know about compatibility and integration with Meteo
  Phone.
---

# For Developers

### Zero Configuration Required

Meteo Phone is built to work **out of the box** with your existing server setup. No begging other developers for compatibility patches.

#### Why It Just Works

| Feature    | How We Handle It                            |
| ---------- | ------------------------------------------- |
| **Garage** | Reads directly from `player_vehicles` table |
| **Bank**   | Uses default QBCore bank functions          |
| **Jobs**   | Uses default QBCore job system              |
| **Emails** | Full `qb-phone` export compatibility        |

> Most script developers already support default QBCore/QBox scripts **99% of the time**. Simply use the default qb scripts option in their configs.

***

### Requirements

#### Core Dependencies

| Dependency               | Purpose                                                                                                                                                 |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ox\_inventory**        | Required for SIM card slots and metadata                                                                                                                |
| **ox\_target**           | Phone shop interactions                                                                                                                                 |
| **ox\_lib**              | Menus, callbacks, and UI components                                                                                                                     |
| **screencapture**        | Camera and gallery photos                                                                                                                               |
| **meteo-keybinddisplay** | Keybind UI integration (Note this is [free script](https://docs.meteofivem.net/paid-scripts/meteo-phone/installation-guide#install-required-resources)) |
| pma-voice                | For voice                                                                                                                                               |

We leverage ox\_lib for menus, context menus, callbacks. This provides a optimized experience with minimal performance impact.

**Why ox\_inventory?** We use SIM card slots for phone numbers. Only ox\_inventory supports custom advanced stash exports with metadata properly, enabling multiple phone numbers and SIM swapping.

***

### Export Compatibility

#### qb-phone Email Event

Scripts using qb-phone's email event work without any changes:

```lua
-- Your existing qb-phone code works as-is
TriggerServerEvent('qb-phone:server:sendNewMail', {
    sender = 'Los Santos Police',
    subject = 'Citation Notice',
    message = 'You have an unpaid fine.'
})
```

#### Direct Export

For new integrations, use our export:

```lua
exports['meteo-phone']:SendEmailToPhone(phoneSerial, sender, subject, content)
```

**Zero migration effort** - your existing scripts just work.

***

### Database

We use the standard `player_vehicles` table for garage data. No custom vehicle tables or complex integrations needed.

```sql
-- We read from the same table everyone uses
SELECT * FROM player_vehicles WHERE citizenid = ?
```

***

### Need Help? **Discord Support Available**

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)

***

### Quick Summary

* Works with all default QBCore/QBox scripts
* ox\_inventory required (SIM slot support)
* qb-phone exports supported for easy migration
* Uses standard `player_vehicles` table
* No third-party compatibility patches needed
* Active Discord support
