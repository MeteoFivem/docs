---
description: >-
  Meteo hustling - wash folded cash through street buyers, unlocked by a dealer
  and run from the Grindr phone app, script designed exclusively for the Meteo
  V2 package.
---

# Meteo Hustling

This is a guide about testing the Meteo V2 hustling script designed exclusively for the Meteo V2 package. Turn your dirty `meteo_foldedcash` into clean cash by meeting street buyers, all run from the Grindr app on your phone.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* A phone - check out [meteo-phone](../meteo-phone/) guide
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Hustling

### Getting the App

{% stepper %}
{% step %}
Find the dealer in the city, point target at him and click **Talk**
{% endstep %}

{% step %}
Choose **Put me on**. The app costs $5000 in clean cash, so make sure you have it on you
{% endstep %}

{% step %}
That's it - the Grindr app is now on your phone. You only need to do this once
{% endstep %}
{% endstepper %}

### Washing Cash

{% stepper %}
{% step %}
Get some dirty cash. `/giveitem yourid meteo_foldedcash 500`. Buyers take at least 100 so you need at least that much to go online
{% endstep %}

{% step %}
Open Grindr on your phone and go online. The app looks for a buyer for a few seconds, then gives you a meeting spot on your GPS. If every spot is busy you get put in line
{% endstep %}

{% step %}
Get to the meeting spot within 10 minutes. The buyer will be waiting for you there
{% endstep %}

{% step %}
Point target at the buyer and click **Talk business**. They make you an offer - how much dirty cash they take and how much clean cash you get back
{% endstep %}

{% step %}
Pick **Deal** to take it, **Push for more** to haggle (once you unlock the Smooth Talker perk) or **Walk away**. The offer only stays on the table for 60 seconds
{% endstep %}

{% step %}
After the hand-off you get clean cash in your pocket. You can also accept or decline the offer straight from the Grindr app
{% endstep %}
{% endstepper %}

> There is a 35% chance police get alerted on meteo-mdt when a deal goes through. After a deal you have to wait 10 minutes before the next one, and if a deal does not happen (you miss it or walk away) you have a 3 minute cool off

* At least 1 police officer has to be on duty before anyone can go online
* Buyers pay 70% to 105% of the dirty cash value, rolled per deal

### Leveling Up

* Every finished deal gives XP to the **Hussling** line in [meteo-perks](../meteo-perks/) (15 XP per deal plus 5 XP for every 1000 clean cash)
* Perks make buyers find you faster (Known Face, On Speed Dial), pay more (Good Rep, High Roller), take more per deal (Bigger Bags, Kingpin), let you haggle (Smooth Talker), lower the police chance (Low Profile), shorten the wait between deals (Fast Turnaround) and get you tips (Regulars)

***

## Installation

{% hint style="warning" %}
Read this if you are setting up the script on your own server.
{% endhint %}

{% stepper %}
{% step %}
#### Database

The script creates its own tables on start. If you prefer a manual install, run `install/meteo_hussling.sql`. It also seeds one default dealer, and running it again never undoes changes made in game
{% endstep %}

{% step %}
#### Meeting Spots

Meeting spots are not seeded. Open the admin menu and go to Script Settings > Creator > Hussling, add a **Meeting area** and place the spots where buyers should wait. Without at least one spot nobody can go online
{% endstep %}

{% step %}
#### Items

No new items are needed. Buyers take `meteo_foldedcash`, which is already in the package
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
The app price, police on duty, police alerts, timers, XP, haggling, police chance, tips, what buyers take (items, prices, amounts and unlock levels) and buyer models are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit dealers and meeting areas in-game with the Hussling creator.
{% endhint %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
