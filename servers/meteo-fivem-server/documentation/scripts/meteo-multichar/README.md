---
description: >-
  Meteo multichar - character selection and creation with cinematic animations
  designed exclusively for the meteo fivem server.
---

# Meteo Multichar

This is a guide about testing the meteo fivem multi-character selection and creation with cinematic animations designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Character Selection

* when you join the server you will see the character selection screen with cinematic camera animation
* you can see all your character slots (default 6 slots) in a grid
* each character card shows name, job, cash, bank, last played time, state id, gender, birthdate and nationality
* click on a character to preview them and click play to load in

***

## Testing Character Creation

* click on an empty slot and click create button
* fill out the form - first name, last name, gender, birthdate and nationality
* names have a max of 7 characters each (configurable)
* try putting offensive words to see blacklist filter working
* after creating character you will get starter items automatically (phone, sim card, id card, drivers license)

### Apartment Selection (New Characters)

* after creating a new character you will see apartment selection on a bus stop screen
* it shows real-time room availability for each apartment complex
* you will get a free starting apartment

### Spawn Selection (Existing Characters)

* when loading an existing character you will see spawn selection on a bus stop screen
* you can choose from last location, preset locations (WiWang Hotel, LSPD, Los Santos Customs, Airport, Gym, Blaine County, Paleto Bay)
* if your character is jailed you will be forced to spawn at prison - cant choose other locations
* use **arrow keys** to browse and **enter** to confirm

***

## Testing Delete Character

* click on a character and click delete button
* a confirmation popup will appear
* delete can be set to admin-only on config (default is admin only)

***

## Admin Commands

* `/charslots add license:xxxxx 2` - add 2 extra character slots to a player
* `/charslots remove license:xxxxx` - remove extra slots from a player
* `/charslots view` - see all players with extra slots (shows in server console)
* `/logout` - go back to character selection (admin/god only)
* `/deletechar citizenid` - force delete any character (god only, useful for corrupted characters)

***

## Good to Know

* cinematic camera animation, orbit speed, zoom, shake and all camera settings are fully configurable on our config
* starter items, max name length, blacklisted words, default slots and nationality list are all configurable
* character selection screen shows server name and logo. you can change them after your get the server :)
* spawn locations and prison spawn coords are fully configurable
* connected with [meteo-apartments](../meteo-apartments/) for starting apartment selection
