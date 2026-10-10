---
description: >-
  Meteo search vehicles - search vehicles for loot script designed exclusively
  for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-searchvehicles/
---

# Meteo Search Vehicles

This is a guide about testing the Meteo V2 vehicle search script designed exclusively for the Meteo V2 package.

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

## Testing Vehicle Search

{% stepper %}
{% step %}
First of all get `screwdriverset` item. Use /giveitem or admin menu, or you can get it from the hardware store (its called toolkit)
{% endstep %}

{% step %}
Find a vehicle, lockpick its doors and get in the driver seat (no one else can be in the vehicle)
{% endstep %}

{% step %}
Now open inventory and use screwdriverset item and now you can search the vehicle and get items :)
{% endstep %}

{% step %}
Complete the etiming minigame from [meteo-minigames](../meteo-minigames/) (press E as the needle passes each point, medium difficulty by default)
{% endstep %}

{% step %}
You will get 1-3 items based on rarity tables. The loot opens in a stash, and if you leave something behind you can search the same vehicle again to reopen it
{% endstep %}
{% endstepper %}

> If you fail there is 80% chance police gets alerted and the screwdriverset loses durability (25 per fail, it breaks at 0)

* Also drops fingerprint (60% chance) unless wearing gloves
* Super cars give better loot (2x multiplier)

### Items You Can Get

* **common** - water\_bottle, coffee, fitbit, joint, meteo\_foldedcash ($50-200), metalscrap, plastic, meteo\_chopcontract\_easy
* **uncommon** - tablet, screwdriverset, oxy, laptop, radioscanner, meteo\_chopcontract\_medium, meteo\_hr\_oldkeys
* **rare** - tenkgoldchain, diamond\_ring, goldchain, rolex, meteo\_chopcontract\_premium, meteo\_chopcontract\_highend

### Cant Search

* Police vehicles, emergency vehicles, military, helicopters, planes, boats, trains

### Selling Items

* You can sell stolen items at the pawnshop. Check out [meteo-pawnshop](../meteo-pawnshop/) testing guide for more info
* Chop contracts can be used at chop shop. Check out [meteo-chopshop](../meteo-chopshop/) testing guide

***

## Good to Know

{% hint style="success" %}
Common, uncommon and rare loot, police alerts, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-minigames/" %}
[meteo-minigames](../meteo-minigames/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
