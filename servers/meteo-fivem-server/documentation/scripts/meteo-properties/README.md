---
description: >-
  Meteo properties - advanced properties with ingame creator script
  designed exclusively for the meteo fivem server.
---

# Meteo Properties

This is a guide about testing the meteo fivem advanced properties script with ingame creator designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Properties

{% stepper %}
{% step %}
**Checking Available Properties**

Use `/tp -709.6076, 267.8896, 83.1079` to go to property broker NPC and check available properties and locate them (all these locations are configurable)
{% endstep %}

{% step %}
**Creating a Property**

Use `/createhouse` command in chat and open the property creator menu. you can create shell houses (so this is for unlimited houses). and also mlo creator is for mlos which you can walk and access them without needing to teleport. after creating the property use f1 menu and access its furnishing menu

{% hint style="warning" %}
`/createhouse` is an admin command and only works with proper permissions.
{% endhint %}
{% endstep %}

{% step %}
**Furnishing**

Furnish the property as you want - you can place up to 150 furniture items per property (configurable). also put tablet using furnish to access and manage the property
{% endstep %}

{% step %}
**Managing Property**

You can add members to your property with different roles:
* **Manager** (limit 1) - can access door, garage, upgrades, stash, wardrobe, furnish
* **Keyholder** (limit 2) - can access door, garage, stash, wardrobe, furnish
* **Guest** (limit 2) - door access only

Member limits can be upgraded (small/medium/large/unlimited)
{% endstep %}

{% step %}
**Security System**

Properties have 6 security levels you can upgrade:
* Level 1 (Basic) - easy lockpick
* Level 2 ($5,000) - easy/medium lockpick
* Level 3 ($15,000) - medium lockpick, 5min auto-lock, police alerts
* Level 4 ($30,000) - hard lockpick, 1min auto-lock
* Level 5 ($50,000) - hard lockpick, 30s auto-lock, anti-burglary
* Level 6 ($100,000) - hard lockpick, 15s auto-lock, anti-burglary, anti-raid
{% endstep %}

{% step %}
**Real Estate Job**

Set your job to realestate: `/setjob yourid realestate 4`. now go to any available property and check if realestate agents can lock and unlock doors of available houses

{% hint style="warning" %}
`/setjob` is a testing command and only works on our testing server.
{% endhint %}
{% endstep %}

{% step %}
**Lockpicking and Police Raid**

To test lockpicking spawn a `lockpick` or `advancedlockpick` item and try to break in. to test police raid (stormram) set your job to police grade 3+: `/setjob yourid police 3` and spawn `police_stormram` item
{% endstep %}
{% endstepper %}

***

## There Are More Advanced Things

* There are more advanced things. please check out the exclusive video and make sure to check them all :)
* Max 20 properties per player (configurable)
* Selling gives back 70% of purchase price

***

## Good to Know

{% hint style="success" %}
All locations, security levels, member limits, prices and settings are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}
