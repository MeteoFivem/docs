---
description: >-
  Meteo misc - vehicle push, crouch, consumables, diving gear and more
  designed exclusively for the meteo fivem server.
---

# Meteo Misc

This is a guide about testing the meteo fivem server misc features.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Features

### Push Vehicle

* after vehicle engine dead or body has lot of damage or fuel low then you can point target to vehicle and push the vehicle
* use A and D to turn left and right while pushing and E to stop push

### Seat Shuffle

* use **O** key to shuffle to other side of the seat. so no need to use f1 menu and change seats everytime

### Vehicle Shooting (First Person Aim)

* get `/giveitem yourid weapon_pistol 1` and use `/car adder` and shooting inside vehicle it will update the shoot camera to first person aim (similar to prp)
* works with bikes, helicopters, boats and normal vehicles

### Zoom Camera

* you can use mouse wheel btn to zoom the camera

### Crouch

* use **K** key to toggle crouch
* crouch animation syncs with other players too

### Meditation

* go to `/tp 2460.56, 3777.03, 42.03` and use E to meditate
* meditation relieves stress for your character
* there are 7 meditation locations around the map

### Consumables (Food, Drinks, Drugs)

* these are the default QBCore consumable items but with proper animations and effects
* test some of these:
  * `/giveitem yourid sandwich 1` - food with eating animation
  * `/giveitem yourid water_bottle 1` - drink with bottle animation
  * `/giveitem yourid coffee 1` - drink with cup animation
  * `/giveitem yourid beer 1` - alcohol with drunk effect and BAC for breathalyzer
  * `/giveitem yourid joint 1` - smoking with smoke particles and prop
* alcohol items add BAC (blood alcohol content) which works with police breathalyzer
* drug items have special screen effects and speed boosts

### Diving Gear

* spawn `diving_gear` item and use it to equip diving suit with oxygen tank
* go underwater and your oxygen drains slowly
* you can hear breathing sounds while diving
* spawn `diving_fill` item to refill your oxygen tank
* oxygen level is saved on the item so it remembers how much you have left

### Parachute

* spawn `parachute` item and use it to equip
* jump from somewhere high and deploy it

### Elevator

* there is an elevator at city hall. go near and press E to use it

### AFK Kick

* if a player is afk for 15 minutes they get kicked automatically
* admin and god groups are immune to this

***

## Good to Know

* all features like vehicle push damage threshold, zoom settings, meditation locations, afk kick time and consumable effects are configurable on our config. you can change them once you get the server. we will guide you :)
