---
description: >-
  Meteo dispatch - 911 calls, panic buttons and auto alerts script
  designed exclusively for the meteo fivem server.
---

# Meteo Dispatch

This is a guide about testing the meteo fivem dispatch script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Dispatch

### As Police/EMS

* set your job: `/setjob yourid police 4` or `/setjob yourid ambulance 4`
* open dispatch using **F6** keybind or `/dispatch` on chat
* you can see active calls, your calls and archived calls
* use the dispatch chat to communicate with other officers on dispatch
* when a new alert comes in press **J** to accept it or use arrow keys to navigate alerts

### Making a 911 Call (As Civilian)

* you need a phone item in your inventory to make 911 calls
* use these commands on chat:
  * `/911 your message here` - emergency call (goes to police and ems)
  * `/911e your message here` - medical emergency (goes to ems only)
  * `/911a your message here` - anonymous tip (caller info is hidden)
  * `/311 your message here` - non-emergency call

### Panic Buttons (As Police)

* `/10-78` - officer needs assistance (high priority alert)
* `/10-99` - officer down (emergency alert)
* also can use f1 menu to do these alerts

### Auto Alerts

* shooting a weapon will automatically trigger a dispatch alert to police (30s cooldown)
* shooting from inside a vehicle also triggers a separate alert
* silenced weapons dont trigger alerts

### Dispatch UI Features

* you can attach/detach yourself to calls
* mark call location on the map
* archive calls when done
* search and filter calls by priority
* see all responding units on each call

***

## Good to Know

* all dispatch settings, keybinds, alert sounds, auto alert triggers and job access are configurable on our config. you can change them once you get the server. we will guide you :)
* connected with our crime system, [meteo-policejob](../meteo-policejob/), [meteo-medicaljob](../meteo-medicaljob/) and more - when crimes happen they automatically send dispatch alerts
* callsigns can be set by boss grade using `/setcallsign playerid callsign`
