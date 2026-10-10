---
description: >-
  Meteo shops - shops across the map with job-restricted items, MDT
  license-restricted items and open stores, built in game with the creator,
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-shops/
---

# Meteo Shops

This is a guide about testing the Meteo V2 shops script designed exclusively for the Meteo V2 package. All the shops across the map with three restriction types: job-restricted items, license-restricted items (like the weapon license from the MDT), and open-to-all stores. Every shop is built in game with the creator.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Job Restricted Items (Hardware Store)

{% stepper %}
{% step %}
**Go to hardware store**

Use `/tp 45.68, -1749.04, 29.61, 53.13` to go to the hardware store
{% endstep %}

{% step %}
**Test with mechanic job**

Use `/setjob yourid mechanic 4` and check if advancedrepairkit shows up in the shop
{% endstep %}

{% step %}
**Test with different job**

Now change your job to something else like `/setjob yourid police 1` and check if advancedrepairkit is removed. repairkit requires the `mechanic` or `police` job, advancedrepairkit requires `mechanic` only
{% endstep %}

{% step %}
**Verify**

Make sure job restricted items show/hide correctly when you switch jobs. If a shop has nothing you can buy, it tells you why - wrong job, missing license, or nothing on the shelf
{% endstep %}
{% endstepper %}

***

## Testing License Restricted Items (Ammunation)

{% stepper %}
{% step %}
**Go to ammunation**

Use `/tp 809.68, -2159.13, 29.62, 1.43` to go to ammunation
{% endstep %}

{% step %}
**Test without weapon license**

Without a valid Weapon License you should NOT see any pistols, guns or ammo in the shop
{% endstep %}

{% step %}
**Get the license**

Get a Weapon License issued on your citizen profile in the MDT, and carry the physical `meteo_license` card for it. Check [meteo-mdt](../meteo-mdt/) for how licenses are issued
{% endstep %}

{% step %}
**Test with weapon license**

With a valid license and the card in your inventory you should now see the pistols and ammo. Try leaving the card behind, or get the license suspended or revoked in the MDT - the guns disappear straight away
{% endstep %}

{% step %}
**Check the weapon registry**

Buy a gun and look it up in the MDT. Every firearm sold is filed in the weapon registry to the buyer, with the shop and the area it was bought in
{% endstep %}
{% endstepper %}

***

## Testing Shop Creator

{% stepper %}
{% step %}
**Open the creator**

Open the admin menu, go to Script Settings and pick Shops. You get the full list of every shop on the server
{% endstep %}

{% step %}
**Build a shop**

Add a shop and set its name, clerk model, clerk scenario and target icon. Leave the clerk empty and the shop opens from a zone instead
{% endstep %}

{% step %}
**Add stock**

Add products with item, price and stock. A job or a license on a row limits who can buy it, empty sells to anyone. Several jobs can be set with a comma, like `mechanic,police`
{% endstep %}

{% step %}
**Add branches**

Add branches by standing where the clerk should go. All branches share the same stock. A branch marked robbable also gets its registers and grabs placed
{% endstep %}

{% step %}
**Save**

Set the map blip and save. The shop updates live with no restart. You can also export, import and save presets of your shops to share them
{% endstep %}
{% endstepper %}

***

## Other Shops

There are many more shops across the map: 24/7 supermarkets, LTD Gasoline, Rob's Liquor, pharmacy, Smoke On The Water, leisure shop, Sea Word, casino bar, mechanic shop, ambulance shop. Pretty simple, just check them out on the map and buy stuff :)

***

## Good to Know

{% hint style="success" %}
Shops support job restrictions (per product or per branch), MDT license restrictions and no restriction (open to all). Some shops are job-locked entirely (ambulance shop, mechanic shop). Public stores can charge the Shop Purchase tax the mayor sets in the MDT. The Haggling perk line in meteo-perks gives discounts at all shops. Add or edit shops in-game with the Shops creator in the admin menu ([meteo-manage](../meteo-manage/)) - stock, prices, job and license restrictions, tax, branches, robbable registers and blips. No code editing needed, and your changes survive script updates. Options like requiring the physical license card or filing guns in the weapon registry still live in the config.
{% endhint %}
