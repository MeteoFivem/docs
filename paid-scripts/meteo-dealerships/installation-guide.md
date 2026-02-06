---
description: >-
  Installation guide for Meteo Dealerships. Follow all steps carefully to ensure
  proper setup on your server.
---

# Installation guide

{% hint style="info" %}
Purchase This Script from: [Meteo Dealerships](https://meteo.tebex.io/)
{% endhint %}

{% stepper %}
{% step %}
#### Download the Resource

* Visit [Cfx Portal](https://portal.cfx.re/)
* Login and go to assets tab
* Find **"Meteo Dealerships"** and download it
{% endstep %}

{% step %}
#### Install the Files

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your **server.cfg** file
* Add this line: `ensure [meteostudios]`
{% endstep %}

{% step %}
#### Install Required Resources

Download and update these resources (get the latest versions)

* [ox\_lib](https://github.com/overextended/ox_lib/releases) - Required for callbacks, locale, and UI
* [oxmysql](https://github.com/overextended/oxmysql/releases) - Required for database queries
* [meteo-keybinddisplay](https://github.com/MeteoStudios/meteo-keybinddisplay) - Required for keybind prompts

Make sure they're all added in your server.cfg before meteo-dealerships:

```
ensure ox_lib
ensure oxmysql
ensure meteo-keybinddisplay
ensure [meteostudios]
```
{% endstep %}

{% step %}
#### Setup Database

* Open **HeidiSQL**
* Find the file: `meteo-dealerships/install/meteo_dealerships.sql`
* Run this SQL file in your database

This creates the following tables:

* `meteo_dealerships` - Dealership ownership and balance
* `meteo_dealership_vehicles` - Vehicle catalog
* `meteo_dealership_inventory` - Stock for owned dealerships
* `meteo_dealership_employees` - Employee records
* `meteo_dealership_sales` - Sales history
* `meteo_dealership_favorites` - Player favorites
* `meteo_dealership_finance` - Finance records
* `meteo_dealership_logs` - Activity logs
{% endstep %}

{% step %}
#### Remove Old Dealership Scripts

{% hint style="warning" %}
**Important:** You must remove your existing dealership scripts to avoid conflicts.
{% endhint %}

**Common scripts to remove:**

| Script            | Action                                |
| ----------------- | ------------------------------------- |
| `qb-vehicleshop`  | Delete folder, remove from server.cfg |
| `qbx_vehicleshop` | Delete folder, remove from server.cfg |

**Steps:**

1. Stop your server
2. Delete the old dealership folder from your resources
3. Remove the `ensure` line from your **server.cfg**
4. Start your server with meteo-dealerships
{% endstep %}

{% step %}
#### Configure Dealerships

1. Open `meteo-dealerships/shared/config.lua`
2. Edit the `Config.dealerships` table to set up your locations
3. Configure `categories` and `shops` for each dealership
4. Set up blips, spawn points, and showroom displays

See [Adding New Dealership](for-developers/adding-a-new-dealership.md) for detailed configuration options.
{% endstep %}

{% step %}
#### Import Vehicles

1. Make sure your QBCore `shared/vehicles.lua` has vehicles with `shop` field
2. Start your server
3. Use `/dealeradmin` command in-game
4. Select a dealership and click "Import Vehicles"
5. Vehicles matching the dealership's `categories` and `shops` config will appear

See [Adding New Vehicles](for-developers/adding-new-vehicles.md) for QBCore vehicle setup.
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* Installed in `[meteostudios]` folder
* Added to server.cfg
* Installed ox\_lib, oxmysql, meteo-keybinddisplay
* Ran SQL file in database
* Removed old dealership script
* Configured dealership `categories` and `shops`
* Imported vehicles via admin panel

***

## Next Steps

Now the installation is complete. Configure your dealerships and set up owners via the admin panel.

* [Adding New Dealership](for-developers/adding-a-new-dealership.md) - Configure locations and settings
* [Adding New Vehicles](for-developers/adding-new-vehicles.md) - Import vehicles from QBCore
* [Useful Commands](useful-commands.md) - Admin commands reference

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
