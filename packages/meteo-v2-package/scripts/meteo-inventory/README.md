---
description: >-
  Meteo inventory - inventory with item rarity, clothing, armor, backpacks,
  character status and perks designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-inventory/
---

# Meteo Inventory

This is a guide about testing the Meteo V2 inventory script designed exclusively for the Meteo V2 package. this inventory comes with item rarity display which you can customize and add more. clothing support, armor support, health system support, a character status tab and your perks all in one place.

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

## Testing Inventory

{% stepper %}
{% step %}
**Opening and Shortcuts**

Open inventory using **TAB** key. hover the keyboard icon on the inventory to see the useful controls (right click for the item menu, **ALT** + click to fast use, **CTRL** + click to fast move a stack, **SHIFT** + drag to split and more). you can use **Q** and **E** to switch between the tabs on the right side - utility, clothing, status and perks (and the other inventory when you open a stash or shop)
{% endstep %}

{% step %}
**Clothing Section**

Go to clothing section and try removing clothing and see if they are updating. go to clothing store and buy clothing and see if its again updating automatically on clothing section slots
{% endstep %}

{% step %}
**Armor System**

Spawn `improved_bodyarmor` and put it on armor slot and it will start putting the armor. then you can see the hud will update with the armor and see the health. now get damages and see if its updating the armor health too. when health is low you can spawn `armor_plate` and use them. it will update the health of armor. you can also remove the armor by just removing armor from the slot
{% endstep %}

{% step %}
**Backpacks**

Inventory supports backpacks. spawn `/giveitem yourid military_backpack 1` and put it to backpack slot and it will show the backpack on your character. you can right click on the backpack item and rename it as you want
{% endstep %}

{% step %}
**Items (Drop, Give, Throw)**

Spawn `water_bottle` and open inventory and right click on water bottle item. click on drop and see if its appearing on the ground and removed from the inventory. point target on water bottle on the ground and pickup that item again. open inventory again and right click and click on give item. when giving you can throw the item or use **E** to give item to nearest player or **Backspace** to cancel it. throw the item and see if its spawning on the throw location
{% endstep %}

{% step %}
**Status Tab**

Switch to the **Status** tab. it shows your physical form from [meteo-gym](../meteo-gym/) (strength, dexterity, endurance and gym energy), every buff and debuff running on you with the time left, your cravings from [meteo-buffs](../meteo-buffs/) and your injuries. use some items like `beer` or `meteo_taco` and see them show up here
{% endstep %}

{% step %}
**Perks Tab**

Switch to the **Perks** tab. perks now live inside the inventory instead of a separate menu. you can see your total level and every perk line grouped by outlaw, hustler, worker, lifestyle and other, with the level, XP bar and the perks each line unlocks. check out [meteo-perks](../meteo-perks/) for more info
{% endstep %}

{% step %}
**Injury Display**

When you get an injury on inventory skeleton it will display with the details
{% endstep %}

{% step %}
**Phone Sim Card**

Items like phone can put sim cards support. right click on phone and click on open and you can put the sim card and check
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Item rarity colors, clothing slots, armor settings and all inventory features are configurable on our config. you can change them once you get the package. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-weaponback/" %}
[meteo-weaponback](../meteo-weaponback/)
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-buffs/" %}
[meteo-buffs](../meteo-buffs/)
{% endcontent-ref %}
