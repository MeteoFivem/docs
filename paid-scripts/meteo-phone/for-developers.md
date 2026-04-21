---
description: >-
  Everything you need to know about compatibility and integration with Meteo
  Phone.
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/hPLkuIrL5TffIt3aasi9/paid-scripts/meteo-phone/for-developers
---

# For Developers

### Zero Configuration Required

Meteo Phone is built to work **out of the box** with your existing server setup. No begging other developers for compatibility patches.

#### Why It Just Works

| Feature | How We Handle It |
|---------|------------------|
| **Garage** | Reads directly from `player_vehicles` table |
| **Bank** | Uses default QBCore bank functions |
| **Jobs** | Uses default QBCore job system |
| **Emails** | Full `qb-phone` export compatibility |

> Most script developers already support default QBCore/QBox scripts **99% of the time**. Simply use the default qb scripts option in their configs.

---

### Requirements

#### Core Dependencies

| Dependency | Purpose |
|------------|---------|
| **ox_inventory** | Required for SIM card slots and metadata |
| **ox_target** | Phone shop interactions |
| **ox_lib** | Menus, callbacks, and UI components |
| **oxmysql** | Database queries |
| **screencapture** | Camera and gallery photos |
| **meteo-keybinddisplay** | Keybind UI integration |

{% hint style="info" %}
**Built on ox_lib ecosystem**

We leverage ox_lib for menus, context menus, callbacks, and notifications. This provides a modern, optimized experience with minimal performance impact.

**Why ox_inventory?** We use SIM card slots for phone numbers. Only ox_inventory supports custom item slots with metadata properly, enabling multiple phone numbers and SIM swapping.
{% endhint %}

---

## Export Compatibility

#### qb-phone Email Event (QBox too)

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

#### prp-bridge Support

We support <a href="https://github.com/ProdigyPRP/prp-bridge" target="_blank">prp-bridge</a> offical prodidy rp scripts bridge. Contact our support to get the file or check our PR.

```lua
-- prp-bridge phone.sendMessage -> DispatchSMSToPlayer
-- prp-bridge phone.sendCoords -> DispatchLocationToPlayer
-- prp-bridge phone.sendNotification -> SendNotificationToPhone
```

### SMS & Location Exports

Send text messages and map coordinates to players programmatically:

```lua
-- Send an SMS from any number (real or system-generated)
exports['meteo-phone']:DispatchSMSToPlayer(serverId, '555-000-0001', 'Your order is ready for pickup.')

-- Send a location pin via SMS
exports['meteo-phone']:DispatchLocationToPlayer(serverId, '555-000-0001', vector3(215.76, -810.12, 30.73), 'Pickup location')

-- Get a player's phone number
local phoneNumber = exports['meteo-phone']:GetActivePhoneNumber(serverId)
```

See [Useful Exports](useful-exports.md) for the full list.

---

## Database

We use the standard `player_vehicles` table for garage data. No custom vehicle tables or complex integrations needed.

```sql
-- We read from the same table everyone uses
SELECT * FROM player_vehicles WHERE citizenid = ?
```

---

## Support

{% hint style="success" %}
**Discord Support**

<a href="https://discord.gg/your-link" target="_blank">Join our Discord</a> for technical support and custom integration help.
{% endhint %}

---

## Quick Summary

- Works with all default QBCore/QBox scripts
- ox_inventory required (SIM slot support)
- qb-phone exports supported for easy migration
- prp-bridge compatible (SMS, notifications, location sharing)
- Uses standard `player_vehicles` table
- No third-party compatibility patches needed
- Active Discord support
