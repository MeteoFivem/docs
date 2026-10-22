---
description: >-
  Meteo crafting tables - recipes with a level system, outdoor and property
  benches built in-game, designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-craftingtables/
---

# Meteo Crafting Tables

This is a guide about testing the Meteo V2 crafting script designed exclusively for the Meteo V2 package.

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

## Testing Crafting

### Outside Locations

There are crafting bench locations outside too:

* `/tp 814.3134, -2431.6831, 20.9912` - general bench
* `/tp 1000.5610, -2182.7073, 29.5516` - weapon attachments bench
* `/tp 992.6163, -2191.4932, 30.5516` - weapons bench

### Inside Property

{% stepper %}
{% step %}
But lets try inside a property. You must own the property. Check out [meteo-properties](../meteo-properties/) if you need one
{% endstep %}

{% step %}
Open the furnishing menu and select the **Crafting Tables** category. Buy and place the benches you want
{% endstep %}

{% step %}
Target the bench and you get 3 options - **Open Crafting**, **Materials** and **Storage**
{% endstep %}
{% endstepper %}

### Crafting

{% stepper %}
{% step %}
Open **Materials** and put the required items in. The materials storage only accepts items that one of that bench's recipes needs, anything else gets refused
{% endstep %}

{% step %}
Open crafting, pick a recipe, set the amount and add it to the queue. Then start crafting
{% endstep %}

{% step %}
When it is done open **Storage** and take your crafted items. The storage is take-only, so it cannot be used to store other items
{% endstep %}
{% endstepper %}

### Crafting Levels

* Recipes are spread across 3 bench types with a level system (level 1 to 10)
* Each craft gives crafting XP and higher levels unlock better recipes
* Recipes range from basic items like bandages (level 1) to weapons and drug tables (higher levels)
* Crafting also gives XP on the **Crafting** line in [meteo-perks](../meteo-perks/), which unlocks faster crafting, a chance to save materials, a chance for double output and more

> Please check the video to see all of them

{% hint style="warning" %}
Want to skip the grind? Use `/setcraftxp yourid 2000` to jump to max level. This command is only available on our showcase server. Also check out [test-commands](test-commands.md) for more details.
{% endhint %}

***

## Testing the Creator

Admins can build recipes and benches in-game. Open the admin menu with **F9** and go to **Script Settings** > **Creator** > **Crafting**. A record is either a recipe or a bench.

{% stepper %}
{% step %}
**Recipe** - pick the item crafted, the craft time, the level needed, the XP given and the materials
{% endstep %}

{% step %}
**Bench** - pick the bench prop and where it stands, and list the recipes it offers. You can also sell the bench in properties with a price and a max per property, so players can buy it from the furnishing menu
{% endstep %}

{% step %}
Save. It applies straight away, no restart needed
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Recipes and benches are editable in-game with the **Crafting** creator, and the perk XP per craft is editable from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* Admins can also see a player's crafting level and give crafting XP from the player profile in the admin menu
