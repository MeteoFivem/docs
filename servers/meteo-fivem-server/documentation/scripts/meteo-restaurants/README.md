---
description: >-
  Meteo restaurants - restaurant script with ingame creator designed exclusively
  for the meteo fivem server.
---

# Meteo Restaurants

This is a guide about testing the meteo fivem restaurant script with ingame creator designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Creating a Restaurant (Admin)

* Use `/restdev` command on chat to open restaurants admin manage menu
* Go to restaurants tab on there you can create new restaurants for your new mlo. For our current mlos we already made them for you. So you dont have to create them again for our current restaurant mlos

### When Creating Restaurant

{% stepper %}
{% step %}
First you have to give name and you can put BLIP SPRITE id from [https://docs.fivem.net/docs/game-references/blips/](https://docs.fivem.net/docs/game-references/blips/) and put that number. Also the color
{% endstep %}

{% step %}
After doing it update WORK RADIUS (Auto clock-out zone in meters)
{% endstep %}

{% step %}
After doing it select all ENABLED CATEGORIES needed for the restaurant
{% endstep %}

{% step %}
Finally click save button
{% endstep %}
{% endstepper %}

### Adding Locations

* After making the restaurant go to locations tab and select the restaurant you made and add all necessary locations
* For example clock and manage location, kitchen, ingredients shop, storage, cooking station, drink station, order counter etc.
* Also on doors tab you can create doorlocks related to the restaurant

***

## Setting Yourself as Owner

{% stepper %}
{% step %}
After doing all go back to Manage Restaurants tab and click on the restaurant you created
{% endstep %}

{% step %}
Scroll to bottom and put your id and click set owner button (use `/id` if you dont know)
{% endstep %}

{% step %}
Then you will be able to access and manage the restaurant like owner and hire players do anything you want
{% endstep %}
{% endstepper %}

***

## Testing the Restaurant

### As Owner/Manager

* Clock in at the clock location
* Hire employees and set their grades:
  * **Employee** (grade 0) - $50 paycheck, can cook and take orders
  * **Supervisor** (grade 1) - $75 paycheck, can clock others in/out
  * **Manager** (grade 2) - $100 paycheck, can hire/fire, view earnings, set commissions
  * **Owner** (grade 3) - full access to everything
* Set commission rate (5% to 25%, default 15%)

### Cooking and Serving

{% stepper %}
{% step %}
Buy ingredients from the ingredients shop location
{% endstep %}

{% step %}
Go to process station to process items (chop, grind, blend)
{% endstep %}

{% step %}
Go to cooking station to cook items (grill, fry, bake, assemble)
{% endstep %}

{% step %}
Go to drink station to make drinks (pour, brew, mix)
{% endstep %}

{% step %}
Check the shop stash to sell items to customers
{% endstep %}
{% endstepper %}

### Also Make Sure to

* Check all unique items that are on the restaurants. There are more than 50+ custom made unique items
* Test the work zone auto clock-out (if you go too far from restaurant you get clocked out)
* Test paycheck system (pays every 10 minutes by default)

***

## Watch the Exclusive Guide Video

> Watch the exclusive guide video to see all advanced features and try them by yourself

***

## Good to Know

{% hint style="success" %}
All restaurant settings, employee grades, paychecks, commission rates, storage sizes and more are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}
