---
description: >-
  Meteo boosting - vehicle boosting script with 4 classes (D to S)
  designed exclusively for the meteo fivem server.
---

# Meteo Boosting

This is a guide about testing the meteo fivem vehicle boosting script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) guide before following this.

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Boosting

### Getting a Contract

* first get `meteo_boostcontract` item. use /giveitem or admin menu to get. also normal players can get this through crates, chopshop too
* now use the meteo\_boostcontract item and it will add boosting contract to the crime tablet. open the tablet and go to the boosting app and see the new contract
* also with perks you can increase chance of getting higher boosting contracts
* you can do this with a group too. follow group guide on [crimetablet](../meteo-crimetablet/) guide and add group members too

### Boost Classes

* **D class** (level 1) - find vehicle, steal it, deliver. 80-160 MTC reward
* **C class** (level 5) - same as D but also need to hack GPS. 200-400 MTC reward
* **A class** (level 7) - fight guards, hack GPS, repaint vehicle. 400-800 MTC reward
* **S class** (level 9) - eliminate guards, hack GPS, repaint. 7500-11000 MTC reward

### Testing S Class Boost

* since we are going to test a S class boost use `/testboost S` command (note this command is only available on the test server. check [test-commands](test-commands.md) for more info)
* click on S class boost contract and you can start boost. also if you want to do with a group you can check the crimetablet group guide

### Doing the Boost

* go to marked location on map and find the vehicle and fight guards and get the vehicle
* lockpick it and get in the vehicle

### Hacking GPS (C/A/S Class)

* you need `trojan_usb`. just use /giveitem or admin to get it. also normal players can get this using crafting and crates
* put trojan\_usb inside the tablet storage. check out the video if you dont know (this part can be done by group member if you have a group)
* after that open the tablet and go to terminal and use `hack` command and hack the gps. check out the testing video :) its not hard. and also minigame is lowered for testing quickly. once you get the server ask from us we will guide you to change its difficulty

### Repainting (A/S Class)

* after hacking GPS you will get a place to repaint the vehicle. go to that location and repaint

### Vin Scratch (Optional - Keep the Vehicle)

* you can spawn `meteo_vinscratch` item using giveitem. put it inside tablet storage and use `revin` command on terminal before dropping off the vehicle
* and then drop off. now you can keep the vehicle by yourself lol
* meteo\_vinscratch for normal players can get using doing crime hunts and with their crates and also chopshop high class contracts. its very very rare item

### Drop Off

* finally deliver the vehicle to the drop off location and get your rewards

***

## Good to Know

* all boost classes, vehicle lists, rewards, GPS hack difficulty, guard settings, repaint locations and level requirements are configurable on our config. you can change them once you get the server. we will guide you :)
* there are 10 experience levels (Runner to Legend). higher levels unlock better contracts
* connected with [meteo-crimetablet](../meteo-crimetablet/) for terminal commands and storage
* connected with [meteo-perks](../meteo-perks/). if you have **Enforcer** specialization - Wheelman gives extra time on boost jobs, Nitro Veins increases race pay, Boost King unlocks higher tier contracts earlier, Speed Demon increases fast finish bonus
* connected with [meteo-dispatch](../meteo-dispatch/) for police alerts
