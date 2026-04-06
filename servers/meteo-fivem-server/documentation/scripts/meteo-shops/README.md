---
description: >-
  Meteo shops - shops across the map with job-restricted items, item-restricted
  items (weapon license) and open stores designed exclusively for the meteo
  fivem server.
---

# Meteo Shops

This is a guide about testing the meteo fivem shops script designed exclusively for meteo server. all the shops across the map with three restriction types: job-restricted items, item-restricted items (like weapon license), and open-to-all stores.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-shops-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Job Restricted Items (Hardware Store)

{% stepper %}
{% step %}
**Go to hardware store**

use `/tp 45.68, -1749.04, 29.61, 53.13` to go to hardware store
{% endstep %}

{% step %}
**Test with mechanic job**

use `/setjob yourid mechanic 4` and check if advancedrepairkit shows up in the shop
{% endstep %}

{% step %}
**Test with different job**

now change job to something else like `/setjob yourid police 1` and check if advancedrepairkit is removed. repairkit requires `mechanic` or `police` job, advancedrepairkit requires `mechanic` only
{% endstep %}

{% step %}
**Verify**

make sure job restricted items show/hide correctly when you switch jobs
{% endstep %}
{% endstepper %}

***

## Testing Item Restricted Items (Ammunation)

{% stepper %}
{% step %}
**Go to ammunation**

use `/tp 809.68, -2159.13, 29.62, 1.43` to go to ammunation
{% endstep %}

{% step %}
**Test without weapon license**

WITHOUT `meteo_weaponlicense` in your inventory: you should NOT see any pistols or guns in the shop
{% endstep %}

{% step %}
**Get the license**

use `/giveitem yourid meteo_weaponlicense` or admin menu items section to get the weapon license
{% endstep %}

{% step %}
**Test with weapon license**

WITH weapon license: you should now see pistols, ammo, and armor in the shop. make sure restricted items appear/disappear based on having the license in inventory
{% endstep %}
{% endstepper %}

***

## Other Shops

there are many more shops across the map: 24/7 supermarkets, ltd gasoline, rob's liquor, pharmacy, weed shop, leisure shop, sea world, casino bar, mechanic shop, ambulance shop. pretty simple just check them out on the map and buy stuff :)

***

## Good to Know

{% hint style="success" %}
shops support three restriction types: requiredJob (per product or per location), requiredItem (must have item in inventory), and no restriction (open to all). requiredJob can be a single job string or array of jobs (e.g. mechanic and police both can buy repairkits). some shops are job-locked entirely (ambulance shop, mechanic shop). all prices, stock amounts, and restrictions are configurable in Config.shops. once you get the server. we will guide you :)
{% endhint %}
