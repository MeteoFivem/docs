---
description: >-
  Meteo ATM skimming - attach card readers to ATMs, skim NPC card data via
  terminal commands, extract and sell data for crypto with 15% police dispatch
  chance designed exclusively for the Meteo V2 se
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-atmskimming/
---

# Meteo ATM Skimming

This is a guide about testing the Meteo V2 atm skimming script designed exclusively for the Meteo V2 package. attach card readers to ATMs, connect via crime tablet terminal commands, skim NPC card data with minigame, extract data to USB (max 10 files per usb), sell to data buyer for crypto and 15% police dispatch chance per capture.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

{% hint style="warning" %}
Make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) testing guide before doing this.
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing ATM Skimming

### Attaching Reader

{% stepper %}
{% step %}
First you need to get `meteo_atm_reader`. you can use giveitem or admin menu to get this. also for normal players they can get this from crafting
{% endstep %}

{% step %}
Go to any atm. lets choose a crowded atm
{% endstep %}

{% step %}
So when you have meteo\_atm\_reader item on inventory it will show option to attach card reader when point target to atm
{% endstep %}
{% endstepper %}

### Setting Up USB

{% stepper %}
{% step %}
Now get `meteo_usb` item too. also players can get this from crafting
{% endstep %}

{% step %}
Now put meteo\_usb to tablet storage. check the video
{% endstep %}
{% endstepper %}

### Skimming

{% stepper %}
{% step %}
After attaching open the crime tablet
{% endstep %}

{% step %}
Open terminal app and type `skim` command on terminal and enter. then it will show the available readers and use its serial with skim command and connect. check out the video. its super easy
{% endstep %}

{% step %}
Now wait for NPC to come to ATM and when NPC comes open the crime tablet and wait for minigame to pop. after minigame comes do it

{% hint style="warning" %}
Since this is testing i have lowered the difficulty of minigames. you can increase them easily once you get the package. we will guide you :)
{% endhint %}
{% endstep %}

{% step %}
After success you can run the same command again and wait for another NPC and repeat the process til you run out of usb storage (max 10 files per usb)
{% endstep %}

{% step %}
Also you can detach atm card reader and stop
{% endstep %}
{% endstepper %}

> There is a 15% chance police gets dispatched per capture

### Extracting Data

{% stepper %}
{% step %}
After skimming, open crime tablet and go to terminal
{% endstep %}

{% step %}
Use `/extract` command on the terminal to extract data from the usb. check the video for better idea. each extract gives you a `meteo_datafile` item ready to sell and wears down the usb a bit
{% endstep %}
{% endstepper %}

### Selling Data

{% stepper %}
{% step %}
Go to data buyer location at `/tp 166.8623, -1088.464, 29.1924`
{% endstep %}

{% step %}
Talk to the npc and sell your `meteo_datafile` items. payment is in crypto (MTC), not cash
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Data file prices, sale stress, fingerprint chance and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit data buyer spots in-game with the Data Buyers creator.
{% endhint %}

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}
