---
description: >-
  Meteo dispatch - 911 calls, panic buttons and auto alerts script designed
  exclusively for the meteo fivem server.
---

# Meteo Dispatch

This is a guide about testing the meteo fivem dispatch script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Dispatch

### As Police/EMS

{% stepper %}
{% step %}
Set your job: `/setjob yourid police 4` or `/setjob yourid ambulance 4`
{% endstep %}

{% step %}
Open dispatch using **F6** keybind or `/dispatch` on chat
{% endstep %}

{% step %}
You can see active calls, your calls and archived calls
{% endstep %}

{% step %}
Use the dispatch chat to communicate with other officers on dispatch
{% endstep %}

{% step %}
When a new alert comes in press **J** to accept it or use arrow keys to navigate alerts
{% endstep %}
{% endstepper %}

### Making a 911 Call (As Civilian)

* You need a phone item in your inventory to make 911 calls
* Use these commands on chat:
  * `/911 your message here` - emergency call (goes to police and ems)
  * `/911e your message here` - medical emergency (goes to ems only)
  * `/911a your message here` - anonymous tip (caller info is hidden)
  * `/311 your message here` - non-emergency call

### Panic Buttons (As Police)

* `/10-78` - officer needs assistance (high priority alert)
* `/10-99` - officer down (emergency alert)
* Also can use f1 menu to do these alerts

### Auto Alerts

* Shooting a weapon will automatically trigger a dispatch alert to police (30s cooldown)
* Shooting from inside a vehicle also triggers a separate alert
* Silenced weapons dont trigger alerts

### Dispatch UI Features

* You can attach/detach yourself to calls
* Mark call location on the map
* Archive calls when done
* Search and filter calls by priority
* See all responding units on each call

***

## Good to Know

{% hint style="success" %}
All dispatch settings, keybinds, alert sounds, auto alert triggers and job access are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* Callsigns can be set by boss grade using `/setcallsign playerid callsign`

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/)
{% endcontent-ref %}

> Connected with our crime system, meteo-policejob, meteo-medicaljob and more - when crimes happen they automatically send dispatch alerts
