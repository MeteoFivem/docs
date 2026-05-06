---
description: >-
  Installation guide for Meteo Prison Bundle. Follow all steps to get the full
  prison system running on your server.
---

# Installation Guide

{% hint style="info" %}
Purchase this bundle from: <a href="https://meteo.tebex.io/" target="_blank">Meteo Studios Tebex</a>
{% endhint %}

{% hint style="warning" %}
**Remove your old prison scripts before installing this bundle.** Resources like `xt-prison` and `qb-prison` will conflict with this bundle. Stop them in your `server.cfg`, delete the folders and clean up any related database tables they used.
{% endhint %}

{% stepper %}
{% step %}
**Download the Resource**

* Visit <a href="https://portal.cfx.re/" target="_blank">Cfx Portal</a>
* Login and go to assets tab
* Find **"Meteo Studios Prison Bundle"** and download it
{% endstep %}

{% step %}
**Install the Files**

* Unzip the downloaded file (`meteo-prison-bundle`)
* You'll see two folders inside: `meteo-jail` and `meteo-jailhud`
* Create a folder called `[meteostudios]` in your resources (if you don't have one)
* Inside `[meteostudios]`, create a folder called `[prison]` to organize the prison resources
* Put both folders inside `[meteostudios]/[prison]/`
* Open your **server.cfg** file
* Add this line: `ensure [meteostudios]`

Your folder structure should look like:

```
resources/
  [meteostudios]/
    [prison]/
      meteo-jail/
      meteo-jailhud/
```

{% hint style="warning" %}
**Folder structure matters.** This organization keeps your server clean and makes managing meteo studios fivem script updates easier.
{% endhint %}

{% hint style="info" %}
Prefer to ensure each script individually instead of bundling? You can skip the `[prison]` folder and add each one to server.cfg manually:

```
ensure meteo-jail
ensure meteo-jailhud
```
{% endhint %}
{% endstep %}

{% step %}
**Install Required Resources**

Download and update these resources (get the latest versions)

* <a href="https://github.com/overextended/ox_lib/releases" target="_blank">ox\_lib</a> - For callbacks, locale and notifications
* <a href="https://github.com/overextended/oxmysql/releases" target="_blank">oxmysql</a> - For database

Make sure they're all added in your server.cfg before `[meteostudios]`:

```
ensure ox_lib
ensure oxmysql
ensure [meteostudios]
```
{% endstep %}

{% step %}
**Import the Database**

The jail system uses one table to store confiscated belongings, cash and clothing while a player is locked up.

* Open `meteo-jail/meteo_jail.sql`
* Import it into your server's database (HeidiSQL, phpMyAdmin or any MySQL tool)
{% endstep %}

{% step %}
**Add the Items**

The bundle ships with three items: `prison_shovel`, `meteo_jail_mealbox` and `cigarette`. Add them to your inventory:

* **qb-core/shared/items.lua** - copy from `meteo-jail/install/qbcore/qb-items.md`
* **ox\_inventory/data/items.lua** - copy from `meteo-jail/install/qbox/ox-items.md`

{% hint style="info" %}
`cigarette` is already a default item on most QBCore and ox\_inventory setups. Skip it if you already have it.
{% endhint %}
{% endstep %}

{% step %}
**Add Item Images**

Copy the `prison_shovel.png`, `meteo_jail_mealbox.png` and `cigarette.png` images from `meteo-jail/install/images/` to your inventory images folder:

* **qb-inventory:** `qb-inventory/html/images/`
* **ox\_inventory:** `ox_inventory/web/images/`
{% endstep %}

{% step %}
**Configure Locations**

The bundle ships configured for the <a href="https://fivem.gabzv.com/package/4724793" target="_blank">Gabz Prison MLO</a> at Bolingbroke Penitentiary. If you use that MLO, no changes needed.

If you run a different prison MLO, open the configs and update the coords:

* `meteo-jail/shared/config.lua` - prison zone, spawns, freedom peds, visitation peds, mugshot location
* `meteo-jail/shared/jobs.lua` - prison job ped and work locations
* `meteo-jail/shared/traders.lua` - kitchen worker, smuggler and arms dealer locations

{% hint style="info" %}
The dispatch system auto detects between meteo-dispatch, ps-dispatch and tk\_dispatch. You can force a specific one by setting `Config.dispatchSystem` in `meteo-jail/shared/config.lua`.
{% endhint %}
{% endstep %}

{% step %}
**Restart and Test**

1. Restart your server
2. Use `/jail <id> 10` on a player with the police job to send them in
3. The jailed player should see the prison HUD with their remaining time and reputation
4. Try the prison jobs, traders and the escape system to make sure everything works

{% hint style="success" %}
For a full walkthrough of every feature, see the showcase server testing guide at <a href="../../servers/meteo-fivem-server/documentation/scripts/meteo-jail/" target="_blank">Meteo Jail testing guide</a>.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* Both scripts dropped into `[meteostudios]/[prison]/`
* Added `ensure [meteostudios]` (or each script) to server.cfg
* Installed ox\_lib and oxmysql
* Imported `meteo_jail.sql` into your database
* Added `prison_shovel`, `meteo_jail_mealbox` and `cigarette` items
* Copied item images to inventory images folder
* Configured locations for your chosen prison MLO

***

## Next Steps

* [Changelogs](changelogs.md) - Recent updates

***

## Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
