---
description: >-
  Meteo ATM skimming - atm card reader skimming script
  designed exclusively for the meteo fivem server.
---

# Meteo ATM Skimming

This is a guide about testing the meteo fivem atm skimming script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) testing guide before doing this.

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing ATM Skimming

### Attaching Reader

* first you need to get `meteo_atm_reader`. you can use giveitem or admin menu to get this. also for normal players they can get this from crafting
* go to any atm. lets choose a crowded atm
* so when u have meteo\_atm\_reader item on inventory it will show option to attach card reader when point target to atm

### Setting Up USB

* now get `meteo_usb` item too. also players can get this from crafting
* now put meteo\_usb to tablet storage. check the video

### Skimming

* after attaching open the crime tablet
* open terminal app and type `skim` command on terminal and enter. then it will show the available readers and use its serial with skim command and connect. check out the video. its super easy
* now wait for NPC to come to ATM and when NPC comes open the crime tablet and wait for minigame to pop. after minigame comes do it (note since this is testing i have lowered the difficulty of minigames. you can increase them easily once you get the server. we will guide you :)
* after success you can run the same command again and wait for another NPC and repeat the process til you run out of usb storage (max 10 files per usb)
* also you can detach atm card reader and stop
* there is a 15% chance police gets dispatched per capture

***

## Good to Know

* all minigame difficulty, usb storage limits, capture rates, rewards and dispatch chances are configurable on our config. you can change them once you get the server. we will guide you :)
* connected with [meteo-crimetablet](../meteo-crimetablet/) for terminal commands and storage
* connected with [meteo-dispatch](../meteo-dispatch/) for police alerts
