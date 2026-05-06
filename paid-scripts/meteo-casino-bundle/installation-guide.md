---
description: >-
  Installation guide for Meteo Casino Bundle. Follow all steps to get the full
  casino running on your server.
---

# Installation Guide

{% hint style="info" %}
Purchase this bundle from: <a href="https://meteo.tebex.io/" target="_blank">Meteo Studios Tebex</a>
{% endhint %}

{% stepper %}
{% step %}
**Download the Resource**

* Visit <a href="https://portal.cfx.re/" target="_blank">Cfx Portal</a>
* Login and go to assets tab
* Find **"Meteo Studios Casino Bundle"** and download it
{% endstep %}

{% step %}
**Install the Files**

* Unzip the downloaded file. You'll see five folders inside: `meteo-casinocashier`, `meteo-roulette`, `meteo-blackjack`, `meteo-luckywheel` and `meteo-casinoannounce`
* Drop all five folders into your `[meteostudios]` folder (or your existing resource folder)
* Open your **server.cfg** file
* If you already have `ensure [meteostudios]`, all five scripts will load with the bundle
* Otherwise add each one individually:

```
ensure meteo-casinocashier
ensure meteo-roulette
ensure meteo-blackjack
ensure meteo-luckywheel
ensure meteo-casinoannounce
```
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
**Add the Casino Chips Item**

The whole bundle uses one shared item called `casinochips`. Add it to your inventory:

* **qb-core/shared/items.lua** - copy from `meteo-casinocashier/install/qbcore/qb-items.md`
* **ox\_inventory/data/items.lua** - copy from `meteo-casinocashier/install/qbox/ox-items.md`
{% endstep %}

{% step %}
**Add Item Images**

Copy the `casinochips.png` image from the `install/images` folder to your inventory images folder:

* **qb-inventory:** `qb-inventory/html/images/`
* **ox\_inventory:** `ox_inventory/web/images/`
{% endstep %}

{% step %}
**Configure Locations**

The bundle ships configured for the **default GTA Online casino interior**. If you use that interior, no changes needed.

If you run a different casino MLO (gabz, custom rework, etc.), open each config and update the coords:

* `meteo-casinocashier/shared/config.lua` - cashier ped and interaction zone
* `meteo-roulette/shared/config.lua` - roulette table positions
* `meteo-blackjack/shared/config.lua` - blackjack table positions
* `meteo-luckywheel/shared/config.lua` - lucky wheel and vehicle podium
* `meteo-casinoannounce/config.lua` - announcer ped position

{% hint style="info" %}
Each table in roulette and blackjack has a `preset` (junior, standard, vip / junior, normal, high) that controls bet limits and prop texture. Change the preset to match the table tier you want at that location.
{% endhint %}
{% endstep %}

{% step %}
**Restart and Test**

1. Restart your server
2. Walk to the casino cashier and buy some `casinochips`
3. Walk up to a roulette or blackjack table to start a round
4. Spin the lucky wheel once a day for prizes
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* All five scripts dropped into `[meteostudios]` folder
* Added `ensure [meteostudios]` (or each script) to server.cfg
* Installed ox\_lib and oxmysql
* Added `casinochips` item to inventory
* Copied chip image to inventory images folder
* Configured locations for your chosen casino MLO

***

## Next Steps

* [Changelogs](changelogs.md) - Recent updates

***

## Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
