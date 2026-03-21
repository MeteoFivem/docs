---
description: >-
  Meteo restaurants - restaurant script with ingame creator
  designed exclusively for the meteo fivem server.
---

# Meteo Restaurants

This is a guide about testing the meteo fivem restaurant script with ingame creator designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Creating a Restaurant (Admin)

* use `/restdev` command on chat to open restaurants admin manage menu
* go to restaurants tab on there you can create new restaurants for your new mlo. for our current mlos we already made them for you. so you dont have to create them again for our current restaurant mlos

### When Creating Restaurant

1. first you have to give name and u can put BLIP SPRITE id from https://docs.fivem.net/docs/game-references/blips/ and put that number. also the color
2. after doing it update WORK RADIUS (Auto clock-out zone in meters)
3. after doing it select all ENABLED CATEGORIES needed for the restaurant
4. finally click save button

### Adding Locations

* after making the restaurant go to locations tab and select the restaurant you made and add all necessary locations
* for example clock and manage location, kitchen, ingredients shop, storage, cooking station, drink station, order counter etc.
* also on doors tab you can create doorlocks related to the restaurant

***

## Setting Yourself as Owner

* after doing all go back to Manage Restaurants tab and click on the restaurant you created
* and scroll to bottom and put your id and click set owner button (use `/id` if you dont know)
* then you will be able to access and manage the restaurant like owner and hire players do anything you want

***

## Testing the Restaurant

### As Owner/Manager

* clock in at the clock location
* hire employees and set their grades:
  * **Employee** (grade 0) - $50 paycheck, can cook and take orders
  * **Supervisor** (grade 1) - $75 paycheck, can clock others in/out
  * **Manager** (grade 2) - $100 paycheck, can hire/fire, view earnings, set commissions
  * **Owner** (grade 3) - full access to everything
* set commission rate (5% to 25%, default 15%)

### Cooking and Serving

* buy ingredients from the ingredients shop location
* go to process station to process items (chop, grind, blend)
* go to cooking station to cook items (grill, fry, bake, assemble)
* go to drink station to make drinks (pour, brew, mix)
* check the shop stash to sell items to customers

### Also Make Sure to

* check all unique items that are on the restaurants. there are more than 50+ custom made unique items
* test the work zone auto clock-out (if you go too far from restaurant you get clocked out)
* test paycheck system (pays every 10 minutes by default)

***

## Watch the Exclusive Guide Video

watch the exclusive guide video to see all advanced features and try them by yourself

***

## Good to Know

* connected with [meteo-phone](../meteo-phone/) for phone integration
* all restaurant settings, employee grades, paychecks, commission rates, storage sizes and more are configurable on our config. you can change them once you get the server. we will guide you :)
