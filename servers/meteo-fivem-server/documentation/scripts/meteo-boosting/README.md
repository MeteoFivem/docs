---
description: >-
  Meteo boosting - vehicle boosting script with 4 classes (D to S)
  designed exclusively for the meteo fivem server.
---

# Meteo Boosting

This is a guide about testing the meteo fivem vehicle boosting script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="warning" %}
Make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) guide before following this.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Boost Classes

| Class | Level | What you do | Reward |
| ----- | ----- | ----------- | ------ |
| **D class** | 1 | find vehicle, steal it, deliver | 80-160 MTC |
| **C class** | 5 | same as D + hack GPS | 200-400 MTC |
| **A class** | 7 | fight guards, hack GPS, repaint | 400-800 MTC |
| **S class** | 9 | eliminate guards, hack GPS, repaint | 7500-11000 MTC |

> There are 10 experience levels (Runner to Legend). higher levels unlock better contracts

***

## Testing Boosting

{% stepper %}
{% step %}
**Get a contract**

first get `meteo_boostcontract` item. use /giveitem or admin menu to get. also normal players can get this through crates, chopshop too

now use the meteo\_boostcontract item and it will add boosting contract to the crime tablet. open the tablet and go to the boosting app and see the new contract

{% hint style="info" %}
also with perks you can increase chance of getting higher boosting contracts. you can do this with a group too - follow group guide on [crimetablet](../meteo-crimetablet/) guide
{% endhint %}
{% endstep %}

{% step %}
**Start an S class boost (for testing)**

since we are going to test a S class boost use `/testboost S` command

{% hint style="warning" %}
this command is only available on the test server. check [test-commands](test-commands.md) for more info
{% endhint %}

click on S class boost contract and you can start boost
{% endstep %}

{% step %}
**Fight guards and get the vehicle**

go to marked location on map and find the vehicle and fight guards and get the vehicle. lockpick it and get in
{% endstep %}

{% step %}
**Hack GPS (C/A/S class)**

you need `trojan_usb`. just use /giveitem or admin to get it. also normal players can get this using crafting and crates

put trojan\_usb inside the tablet storage. check out the video if you dont know (this part can be done by group member if you have a group)

after that open the tablet and go to terminal and use `hack` command and hack the gps. check out the testing video :) its not hard. and also minigame is lowered for testing quickly. once you get the server ask from us we will guide you to change its difficulty
{% endstep %}

{% step %}
**Repaint the vehicle (A/S class)**

after hacking GPS you will get a place to repaint the vehicle. go to that location and repaint
{% endstep %}

{% step %}
**Vin scratch (optional - keep the vehicle)**

you can spawn `meteo_vinscratch` item using giveitem. put it inside tablet storage and use `revin` command on terminal before dropping off the vehicle

and then drop off. now you can keep the vehicle by yourself lol

{% hint style="danger" %}
meteo\_vinscratch for normal players can get using doing crime hunts and with their crates and also chopshop high class contracts. its very very rare item
{% endhint %}
{% endstep %}

{% step %}
**Drop off**

finally deliver the vehicle to the drop off location and get your rewards
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All boost classes, vehicle lists, rewards, GPS hack difficulty, guard settings, repaint locations and level requirements are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/) - for terminal commands and storage
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/) - Enforcer specialization: Wheelman gives extra time on boost jobs, Nitro Veins increases race pay, Boost King unlocks higher tier contracts earlier, Speed Demon increases fast finish bonus
{% endcontent-ref %}

{% content-ref url="../meteo-dispatch/" %}
[meteo-dispatch](../meteo-dispatch/) - for police alerts
{% endcontent-ref %}
