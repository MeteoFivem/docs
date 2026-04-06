---
description: >-
  Meteo misc - vehicle push, crouch, consumables, diving gear and more designed
  exclusively for the meteo fivem server.
---

# Meteo Misc

This is a guide about testing the meteo fivem server misc features.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Features

### Push Vehicle

* After vehicle engine dead or body has lot of damage or fuel low then you can point target to vehicle and push the vehicle
* Use A and D to turn left and right while pushing and E to stop push

### Seat Shuffle

* Use **O** key to shuffle to other side of the seat. So no need to use f1 menu and change seats everytime

### Vehicle Shooting (First Person Aim)

{% stepper %}
{% step %}
Get `/giveitem yourid weapon_pistol 1` and use `/car adder`
{% endstep %}

{% step %}
Shooting inside vehicle it will update the shoot camera to first person aim (similar to prp)

Works with bikes, helicopters, boats and normal vehicles
{% endstep %}
{% endstepper %}

### Zoom Camera

* You can use mouse wheel btn to zoom the camera

### Crouch

* Use **K** key to toggle crouch
* Crouch animation syncs with other players too

### Meditation

{% stepper %}
{% step %}
Go to `/tp 2460.56, 3777.03, 42.03` and use E to meditate
{% endstep %}

{% step %}
Meditation relieves stress for your character

There are 7 meditation locations around the map
{% endstep %}
{% endstepper %}

### Consumables (Food, Drinks, Drugs)

These are the default QBCore consumable items but with proper animations and effects.

Test some of these:

* `/giveitem yourid sandwich 1` - food with eating animation
* `/giveitem yourid water_bottle 1` - drink with bottle animation
* `/giveitem yourid coffee 1` - drink with cup animation
* `/giveitem yourid beer 1` - alcohol with drunk effect and BAC for breathalyzer
* `/giveitem yourid joint 1` - smoking with smoke particles and prop

> Alcohol items add BAC (blood alcohol content) which works with police breathalyzer. Drug items have special screen effects and speed boosts.

### Diving Gear

{% stepper %}
{% step %}
Spawn `diving_gear` item and use it to equip diving suit with oxygen tank
{% endstep %}

{% step %}
Go underwater and your oxygen drains slowly. You can hear breathing sounds while diving
{% endstep %}

{% step %}
Spawn `diving_fill` item to refill your oxygen tank

Oxygen level is saved on the item so it remembers how much you have left
{% endstep %}
{% endstepper %}

### Parachute

* Spawn `parachute` item and use it to equip
* Jump from somewhere high and deploy it

### Elevator

* There is an elevator at city hall. Go near and press E to use it

### AFK Kick

* If a player is afk for 15 minutes they get kicked automatically
* Admin and god groups are immune to this

***

## Good to Know

{% hint style="success" %}
All features like vehicle push damage threshold, zoom settings, meditation locations, afk kick time and consumable effects are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}
