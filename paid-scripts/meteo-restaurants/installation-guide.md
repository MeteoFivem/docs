---
description: >-
  Installation guide for Meteo Restaurants. Follow all steps to get it running
  on your server.
---

# Installation Guide

{% hint style="info" %}
Purchase this script from: [Meteo Restaurants](https://meteo.tebex.io/)
{% endhint %}

{% stepper %}
{% step %}
**Download the Resource**

* Visit [Cfx Portal](https://portal.cfx.re/)
* Login and go to assets tab
* Find **"Meteo Studios Restaurants"** and download it
{% endstep %}

{% step %}
**Install the Files**

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your **server.cfg** file
* Add this line: `ensure [meteostudios]`
{% endstep %}

{% step %}
**Install Required Resources**

Download and update these resources (get the latest versions)

* [ox\_lib](https://github.com/overextended/ox_lib/releases) - For callbacks, locale, and UI
* [oxmysql](https://github.com/overextended/oxmysql/releases) - For database queries
* [meteo-keybinddisplay](https://github.com/MeteoStudios/meteo-keybinddisplay) - For keybind prompts

Make sure they're all added in your server.cfg before meteo-restaurants:

```
ensure ox_lib
ensure oxmysql
ensure meteo-keybinddisplay
ensure [meteostudios]
```
{% endstep %}

{% step %}
**Setup Database**

* Open **HeidiSQL**
* Find the file: `meteo-restaurants/install/meteo_restaurants.sql`
* Run this SQL file in your database
{% endstep %}

{% step %}
**Add Items to QBCore**

Add all restaurant items to your `qb-core/shared/items.lua` or `qbx_core/shared/items.lua` file.

See `docs/items.md` in the resource folder for the full list.

{% hint style="warning" %}
**QBox users:** If you're using ox\_inventory, see the [ox-items.md](../install/qbox/ox-items.md) file instead.
{% endhint %}
{% endstep %}

{% step %}
**Add Item Images**

Copy all images from the `install/images` folder to your inventory images folder:

* **qb-inventory:** `qb-inventory/html/images/`
* **ox\_inventory:** `ox_inventory/web/images/`

{% endstep %}

{% step %}
**Configure Settings**

1. Open `meteo-restaurants/shared/config.lua`
2. Adjust grades, permissions, and paycheck settings
3. Set commission rates, work zones, and order limits
4. Set up item categories for your restaurants

See [For Developers](for-developers/) for more config options.
{% endstep %}

{% step %}
**Create Restaurants In-Game**

1. Start your server
2. Use `/restdev` command in-game to open the admin panel
3. Create a new restaurant - set name, blip, and enabled categories
4. Add locations (clock station, kitchen storage, cooking station, drink station, order counter, etc.)
5. Set yourself as owner and start testing
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* Installed in `[meteostudios]` folder
* Added to server.cfg
* Installed ox\_lib, oxmysql, meteo-keybinddisplay
* Ran SQL file in database
* Added items to QBCore items.lua (or ox\_inventory)
* Copied item images to inventory images folder
* Configured grades and settings
* Created restaurants via admin panel

***

## Next Steps

Installation is done. Create your restaurants and set them up in-game.

* [Adding Items](adding-items.md) - How to add new food and drinks
* [For Developers](for-developers/) - Config and customization
* [Useful Exports](for-developers/useful-exports.md) - Use in other resources

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
