---
description: >-
  Meteo inventory - inventory with item rarity, clothing, armor and backpacks
  designed exclusively for the meteo fivem server.
---

# Meteo Inventory

This is a guide about testing the meteo fivem inventory script designed exclusively for meteo server. this inventory comes with item rarity display which you can customize and add more. clothing support, armor support, health system support with most advanced features.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-inventory-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Inventory

{% stepper %}
{% step %}
**Opening and Shortcuts**

Open inventory using **TAB** key. hover info icon on right top on the inventory and see inventory shortcuts. you can use **E** to switch between clothing section and utility section
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
Item rarity colors, clothing slots, armor settings and all inventory features are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-weaponback/" %}
[meteo-weaponback](../meteo-weaponback/) - for weapon back display
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/) - for injury and health system
{% endcontent-ref %}
