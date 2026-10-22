---
description: >-
  Meteo weapon on back - weapons display on back and carry items script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-weaponback/
---

# Meteo Weapon on Back

This is a guide about testing the Meteo V2 carrying items and weapons on back script designed exclusively for the Meteo V2 package.

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

## Testing Weapons on Back

{% stepper %}
{% step %}
#### Get a weapon
{% endstep %}

{% step %}
Get a weapon using `/giveitem yourid weapon_carbinerifle 1` or using meteo admin menu items section. Get a big weapon like weapon\_carbinerifle so its easy to see.
{% endstep %}

{% step %}
#### Put it on utility slots
{% endstep %}

{% step %}
Put it on the utility (hotbar) slots on the meteo inventory. You can choose any of the 6 utility slots. Press **E** on the inventory to switch to the utility section.
{% endstep %}

{% step %}
#### Check the display
{% endstep %}

{% step %}
It will display on player back. Try walking around, running and getting in vehicles to see it stays attached properly.
{% endstep %}

{% step %}
#### Test equip and unequip
{% endstep %}

{% step %}
Also try equipping and unequipping the weapon and see it appears and disappears.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
The `/giveitem` command is only available on our showcase server so you can quickly spawn weapons.
{% endhint %}

### Try Different Weapons Too

The script supports 30+ weapons. Try some of these:

* Assault rifles - weapon\_carbinerifle, weapon\_assaultrifle
* Sniper rifles - weapon\_sniperrifle, weapon\_heavysniper
* SMGs - weapon\_smg, weapon\_combatpdw
* Shotguns - weapon\_pumpshotgun\_mk2, weapon\_sawnoffshotgun
* Melee - weapon\_bat, weapon\_golfclub, weapon\_machete

Each weapon has its own tuned position so nothing clips through the player. Also works with both male and female character models.

***

## Testing Carry Items

{% stepper %}
{% step %}
#### Spawn the item
{% endstep %}

{% step %}
Spawn `meteo_pizzathis` using `/giveitem yourid meteo_pizzathis 1` and put it into the utility (hotbar) slots and see.
{% endstep %}

{% step %}
#### Check the animation
{% endstep %}

{% step %}
Your character should hold the item with a carrying animation. Walk around and check it looks right.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All weapon positions and carry items are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}
