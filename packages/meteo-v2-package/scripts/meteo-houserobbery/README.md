---
description: >-
  Meteo house robbery - break into houses and clean them out, designed
  exclusively for the meteo fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-houserobbery/
---

# Meteo House Robbery

This is a guide about testing the meteo fivem house robbery script designed exclusively for meteo server.

You get a mark from a fixer, break into the house, and take everything that is not nailed down - jewellery out of drawers, and the TV off the wall if you have a car to put it in.

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
* You need a lockpick - `/giveitem yourid lockpick 1` or `/giveitem yourid advancedlockpick 1`
* Have a look at the [meteo-crimetablet](../meteo-crimetablet/) guide first, this runs as a service from there

***

## Testing House Robbery

### Getting the Job

{% stepper %}
{% step %}
Get the start item with `/giveitem yourid meteo_hr_oldkeys 1`
{% endstep %}

{% step %}
Open the crime tablet and start the **House Call** service. It costs 15 crypto
{% endstep %}

{% step %}
Check your phone. A burner number texts you a meeting spot with a location pin
{% endstep %}

{% step %}
Drive to the pin and hand the old keys over to the fixer waiting there
{% endstep %}

{% step %}
The house gets marked on your GPS. Now you have 30 minutes to get in and clear it out
{% endstep %}
{% endstepper %}

{% hint style="info" %}
You can run this alone or with up to 4 people in a crime tablet group.
{% endhint %}

### Breaking In

{% stepper %}
{% step %}
Target the front door and pick the lock. A lockpick is harder and wears out faster than an advanced lockpick
{% endstep %}

{% step %}
Failing costs you lockpick durability, and a broken lockpick is gone
{% endstep %}

{% step %}
Picking a door has a 60% chance to send a burglary alert to police through [meteo-dispatch](../meteo-dispatch/)
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Some houses have a homeowner inside. Once you pick the door they come at you with whatever is closest - a bat, a knife, sometimes a pistol. Give it a few seconds before you relax.
{% endhint %}

### Looting the House

There are two things worth taking inside.

**Search spots** - target furniture like drawers, cabinets and safes. Pass the search minigame and it opens as a stash with whatever the house rolled. Cash is guaranteed, and then it is down to luck - phones, gold chains, rolexes, diamond rings, lockpicks, or one of the rare pieces.

**Carry props** - the big stuff. TVs, microwaves, printers, coffee machines, VCRs, MP3 docks, kettles and toasters. Target one and lift it.

{% stepper %}
{% step %}
Take a TV with `meteo_hr_tv` and see the carry animation kick in
{% endstep %}

{% step %}
You cannot run or jump while carrying the big ones, and your hands are full until you put it down
{% endstep %}

{% step %}
Try to hand it to someone or throw it down and it refuses - bulky loot goes in a vehicle trunk, nothing else
{% endstep %}

{% step %}
Load it into a car boot, then go back for the next one
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
Every action inside leaves a fingerprint at 60% chance - forcing a door, searching a spot, lifting an item. Wear gloves and you leave nothing. Check the [meteo-evidence](../meteo-evidence/) guide to see what police can do with those prints.
{% endhint %}

### Selling It

* The rare finds - antique pocket watch, ruby, silver locket - sell at the [pawnshop](../meteo-pawnshop/)
* The appliances need a buyer too, so do not bother lifting a TV if you have nowhere to put it

### Finishing

* A timer HUD counts your remaining time, and turns red near the end
* Clear the house and you get 30 crypto and 10 reputation
* In a group everyone gets paid, with members on half the leader's share
* Everyone who took part goes on a 15 minute cooldown

### Achievements

Four achievements track through the [crime tablet](../meteo-crimetablet/):

| Achievement | How to get it | Reward |
| ----------- | ------------- | ------ |
| Breaking In | Complete your first house robbery | 75 crypto |
| Cat Burglar | Complete 10 house robberies | 250 crypto |
| Master Thief | Complete 50 house robberies | 1000 crypto |
| Inside Job | Complete 5 house robberies with a crew | 300 crypto |

***

## Good to Know

{% hint style="success" %}
The houses themselves are built with an in game creator - rooms, doors, loot spots, props and guard spawns are all placed by hand and saved to the database. Loot pool, minigame difficulty, guard behaviour, rewards, cooldown, time limit and dispatch chance are configurable. You can change them once you get the server. We will guide you :)
{% endhint %}

* Completing a robbery gives [meteo-perks](../meteo-perks/) progress, and the Quick Hands perk makes the search minigame easier
* Picking locks adds stress, which ties into [meteo-buffs](../meteo-buffs/)
* Admins can use `/hrcreator` to build a new house

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/)
{% endcontent-ref %}

{% content-ref url="../meteo-pawnshop/" %}
[meteo-pawnshop](../meteo-pawnshop/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-dispatch/" %}
[meteo-dispatch](../meteo-dispatch/)
{% endcontent-ref %}
