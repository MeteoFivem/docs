---
description: >-
  Everything you need to know about integrating Meteo Apartments with your
  scripts.
---

# For Developers

### Works Out of the Box

Meteo Apartments is built for QBCore/QBox and works with your existing server setup. No compatibility patches needed.

#### What We Use

| Feature       | What We Use                           |
| ------------- | ------------------------------------- |
| **Framework** | QBCore/QBox functions                 |
| **Target**    | ox\_target (auto-detected)            |
| **Inventory** | ox\_inventory (auto-detected)         |
| **Zones**     | ox\_lib zones for apartment detection |
| **Doorlock**  | Custom doorlock system                |

***

### Requirements

#### Core Dependencies

| Dependency         | Purpose                         |
| ------------------ | ------------------------------- |
| **ox\_lib**        | Zones, menus, callbacks, and UI |
| **oxmysql**        | Database queries                |
| **interact-sound** | Door sounds and doorbell        |

We leverage ox\_lib zones for apartment detection with optimized performance for 100+ players.

***

### QBX Integration

We have built-in support for QBX-specific features:

#### QBX Garages Integration

Make apartment garages work with qbx\_garages. Simple export integration - no complex setup.

[**QBX Garages Setup Guide**](qbx-garages.md)

#### QBX Starter Apartments

Use Meteo Apartments as your starter apartment system. Replaces qbx\_properties spawn selection.

[**QBX Starter Apartments Setup Guide**](qbx-starter-apartments.md)

***

### Exports

We provide exports for custom integrations. Use these to check apartment access, spawn players, or get apartment data.

[**View All Exports**](useful-exports.md)

***

### Custom System Support

Don't see your garage script, alert script, or spawn script supported? You can easily add support by modifying the `source/` files.

**Currently Supported Scripts:**

| Type         | Supported                                     | Notes                                                                                                                                                                                                                          |
| ------------ | --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Garages**  | meteo-garages, jg-advancedgarages, op-garages | <p>op-garages not fully tested<br><br>for qbx_garages please follow <a href="https://docs.meteofivem.net/paid-scripts/meteo-walkable-apartments-creator/configuration-guide/qbx-garages-integration">integration guide</a></p> |
| **Dispatch** | meteo-dispatch, ps-dispatch, tk\_dispatch     | tk\_dispatch not fully tested                                                                                                                                                                                                  |
| **Phone**    | meteo-phone, high-phone, qb-phone, npwd       | high-phone not fully tested                                                                                                                                                                                                    |
| **Lockpick** | ox\_lib skillCheck (default)                  | Can swap for ps-ui, qb-minigames, custom                                                                                                                                                                                       |

{% hint style="warning" %}
**Not Fully Tested:** Scripts like tk\_dispatch, high-phone, and op-garages were implemented according to their documentation but haven't been fully tested. They may require adjustments.
{% endhint %}

**Where to add custom compatibility:**

| File                                 | What It Handles                                                                       |
| ------------------------------------ | ------------------------------------------------------------------------------------- |
| `client/source/cl_compatibility.lua` | Garage scripts (GetGarageSystem, OpenPropertyGarage, ParkPropertyVehicle)             |
| `client/source/cl_functions.lua`     | Lockpick minigame (LockpickMinigame function)                                         |
| `server/source/sv_alerts.lua`        | Dispatch scripts (GetDispatchSystem, SendDispatch) and phone scripts (GetPhoneSystem) |
| `client/source/cl_alerts.lua`        | Client-side dispatch handlers (ps-dispatch)                                           |
| `server/source/sv_spawn.lua`         | Spawn scripts for multichar                                                           |

**Example: Adding a new garage script**

1. Open `client/source/cl_compatibility.lua`
2. Add your script to `validGarages` table in `GetGarageSystem()`
3. Add detection: `elseif GetResourceState('your-garage') == 'started' then return 'your-garage'`
4. Add your garage's exports/events to `OpenPropertyGarage()` and `ParkPropertyVehicle()`

**Example: Changing lockpick minigame**

1. Open `client/source/cl_functions.lua`
2. Find the `LockpickMinigame` function
3. Replace `lib.skillCheck(difficulty)` with your minigame script (ps-ui, qb-minigames, etc.)

The source files are designed to be modified. If your script isn't auto-detected, you can add it yourself without touching core files.

***

### Built-in Apartment Creator

The in-game creator tool lets you configure apartments without editing Lua files. Point and click to set up doors, zones, and spawn points for any MLO.

**Setup Guides:**

| Guide                                           | What It Does                         |
| ----------------------------------------------- | ------------------------------------ |
| [**Adding New Complex**](adding-new-complex.md) | Configure a new apartment MLO        |
| [**Creating Rooms**](creating-rooms.md)         | Use the in-game creator to add rooms |

No developer knowledge needed to add new apartment buildings.

***

### Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)

***

### Quick Summary

* Works with QBCore/QBox out of the box
* Auto-detects target and inventory systems
* QBX garages and starter apartments supported
* ox\_lib zones for optimized performance
* Exports available for custom integrations
* In-game creator tool for non-developers
