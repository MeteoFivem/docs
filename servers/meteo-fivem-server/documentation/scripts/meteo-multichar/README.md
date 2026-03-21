---
description: >-
  Meteo multichar - character selection and creation with cinematic animations
  designed exclusively for the meteo fivem server.
---

# Meteo Multichar

This is a guide about testing the meteo fivem multi-character selection and creation with cinematic animations designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-multichar-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Character Selection

{% stepper %}
{% step %}
**Join the server**

When you join the server you will see the character selection screen with cinematic camera animation
{% endstep %}

{% step %}
**Browse your characters**

You can see all your character slots (default 6 slots) in a grid. each character card shows name, job, cash, bank, last played time, state id, gender, birthdate and nationality
{% endstep %}

{% step %}
**Select and play**

Click on a character to preview them and click play to load in
{% endstep %}
{% endstepper %}

***

## Testing Character Creation

{% stepper %}
{% step %}
**Create a new character**

Click on an empty slot and click create button. fill out the form - first name, last name, gender, birthdate and nationality. names have a max of 7 characters each (configurable)
{% endstep %}

{% step %}
**Test blacklist filter**

Try putting offensive words to see blacklist filter working
{% endstep %}

{% step %}
**Check starter items**

After creating character you will get starter items automatically (phone, sim card, id card, drivers license)
{% endstep %}
{% endstepper %}

### Apartment Selection (New Characters)

* After creating a new character you will see apartment selection on a bus stop screen
* It shows real-time room availability for each apartment complex
* You will get a free starting apartment

### Spawn Selection (Existing Characters)

* When loading an existing character you will see spawn selection on a bus stop screen
* You can choose from last location, preset locations (WiWang Hotel, LSPD, Los Santos Customs, Airport, Gym, Blaine County, Paleto Bay)
* If your character is jailed you will be forced to spawn at prison - cant choose other locations
* Use **arrow keys** to browse and **enter** to confirm

***

## Testing Delete Character

* Click on a character and click delete button
* A confirmation popup will appear
* Delete can be set to admin-only on config (default is admin only)

***

## Admin Commands

* `/charslots add license:xxxxx 2` - add 2 extra character slots to a player
* `/charslots remove license:xxxxx` - remove extra slots from a player
* `/charslots view` - see all players with extra slots (shows in server console)
* `/logout` - go back to character selection (admin/god only)
* `/deletechar citizenid` - force delete any character (god only, useful for corrupted characters)

{% hint style="warning" %}
These are admin/testing commands and only work with proper permissions.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Cinematic camera animation, orbit speed, zoom, shake and all camera settings are fully configurable on our config. starter items, max name length, blacklisted words, default slots and nationality list are all configurable. character selection screen shows server name and logo. you can change them after your get the server :). spawn locations and prison spawn coords are fully configurable.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-apartments/" %}
[meteo-apartments](../meteo-apartments/) - for starting apartment selection
{% endcontent-ref %}
