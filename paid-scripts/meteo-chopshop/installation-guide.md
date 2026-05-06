---
description: >-
  Installation guide for Meteo Chop Shop. Follow all steps to get it running
  on your server.
---

# Installation Guide

{% hint style="info" %}
Purchase this script from: <a href="https://meteo.tebex.io/" target="_blank">Meteo Studios Tebex</a>
{% endhint %}

{% stepper %}
{% step %}
**Download the Resource**

* Visit <a href="https://portal.cfx.re/" target="_blank">Cfx Portal</a>
* Login and go to assets tab
* Find **"Meteo Studios Chop Shop"** and download it
{% endstep %}

{% step %}
**Install the Files**

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your **server.cfg** file
* If you already have `ensure [meteostudios]`, the script will load with the bundle
* Otherwise add: `ensure meteo-chopshop`
{% endstep %}

{% step %}
**Install Required Resources**

Download and update these resources (get the latest versions)

* <a href="https://github.com/overextended/ox_lib/releases" target="_blank">ox\_lib</a> - For callbacks, locale and notifications
* <a href="https://github.com/overextended/oxmysql/releases" target="_blank">oxmysql</a> - For database queries (if used by integrations)

Make sure they're all added in your server.cfg before `[meteostudios]`:

```
ensure ox_lib
ensure oxmysql
ensure [meteostudios]
```
{% endstep %}

{% step %}
**Add Items to Inventory**

Add the three contract items to your inventory:

* **qb-core/shared/items.lua** - copy from `meteo-chopshop/install/qbcore/qb-items.md`
* **ox\_inventory/data/items.lua** - copy from `meteo-chopshop/install/qbox/ox-items.md`
{% endstep %}

{% hint style="info" %}
The `meteo_chopcontract_easy`, `meteo_chopcontract_medium` and `meteo_chopcontract_highend` items are loot items. Add them as reward drops to your other scripts (vehicle search, drug runs, robberies, dealers, lockpicking, etc.) so players can find them and use them at the chop shop. You can add them anywhere your players normally pick up loot.
{% endhint %}

{% step %}
**Add Item Images**

Copy all images from the `install/images` folder to your inventory images folder:

* **qb-inventory:** `qb-inventory/html/images/`
* **ox\_inventory:** `ox_inventory/web/images/`
{% endstep %}

{% step %}
**Configure Settings**

1. Open `meteo-chopshop/shared/config.lua`
2. Adjust contract tiers, vehicle pools and rewards
3. Set chop shop locations (peds, chop zone, drop zone, blips)
4. Pick a dispatch system (see below)

See [Adding Contracts and Vehicles](adding-contracts.md) for adding more.
{% endstep %}

{% step %}
**Configure Dispatch (Optional)**

Meteo Chop Shop auto-detects your dispatch system. Override it if needed:

```lua
-- shared/config.lua
Config.dispatchSystem = 'auto' -- 'auto', 'meteo-dispatch', 'ps-dispatch', 'tk_dispatch', 'default'

Config.allowedJobs = {
    ['police'] = true,
}

Config.dispatch = {
    enabled = true,
    chance = 30, -- % chance to alert police on chop start
}
```

| Value             | Behavior                                                  |
| ----------------- | --------------------------------------------------------- |
| `auto`            | Picks the first started dispatch resource it finds        |
| `meteo-dispatch`  | Uses Meteo Dispatch via `AddCall` export                  |
| `ps-dispatch`     | Uses ps-dispatch via `ps-dispatch:server:notify` event    |
| `tk_dispatch`     | Uses tk\_dispatch via `addCall` export                    |
| `default`         | Notifies online players with allowed jobs via QBCore      |
{% endstep %}

{% step %}
**Restart and Test**

1. Restart your server
2. Spawn a contract item: `/giveitem meteo_chopcontract_easy 1`
3. Use the contract to activate it, drive a listed vehicle to the chop zone and start chopping
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* Installed in `[meteostudios]` folder
* Added `ensure [meteostudios]` to server.cfg
* Installed ox\_lib and oxmysql
* Added contract items to inventory
* Copied item images to inventory images folder
* Configured locations and dispatch system

***

## Next Steps

* [Adding Contracts and Vehicles](adding-contracts.md) - Add new tiers, vehicles and rewards
* [Changelogs](changelogs.md) - Recent updates

***

## Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
