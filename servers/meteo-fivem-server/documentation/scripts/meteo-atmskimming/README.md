---
description: >-
  Meteo ATM skimming - atm card reader skimming script
  designed exclusively for the meteo fivem server.
---

# Meteo ATM Skimming

This is a guide about testing the meteo fivem atm skimming script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-atmskimming-preview.png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) testing guide before doing this.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
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
So when u have meteo\_atm\_reader item on inventory it will show option to attach card reader when point target to atm
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
Since this is testing i have lowered the difficulty of minigames. you can increase them easily once you get the server. we will guide you :)
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

***

## Good to Know

{% hint style="success" %}
All minigame difficulty, usb storage limits, capture rates, rewards and dispatch chances are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/) - for terminal commands and storage
{% endcontent-ref %}

{% content-ref url="../meteo-dispatch/" %}
[meteo-dispatch](../meteo-dispatch/) - for police alerts
{% endcontent-ref %}
