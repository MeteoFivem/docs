---
description: >-
  Meteo multichar - character selection and creation with cinematic animations
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-multichar/
---

# Meteo Multichar

This is a guide about testing the Meteo V2 multi-character selection and creation with cinematic animations designed exclusively for the Meteo V2 package.

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

After creating character you will get starter items automatically (phone, sim card, id card) and a drivers license
{% endstep %}
{% endstepper %}

### Apartment Selection (New Characters)

* After creating a new character you will see apartment selection on a bus stop screen
* It shows real-time room availability for each apartment complex
* You will get a free starting apartment from [meteo-properties](../meteo-properties/)

### Spawn Selection (Existing Characters)

* When loading an existing character you will see spawn selection on a bus stop screen
* You can choose from last location, preset locations (WiWang Hotel, LSPD, Los Santos Customs, Airport, Gym, Blaine County, Paleto Bay)
* Properties you own show up with a HOME tag and properties you have keys to show up with a KEY tag. picking one spawns you inside it
* If the property was sold or your keys were removed in the meantime you get a notify and land at the default spawn
* If your character is jailed you will be forced to spawn at prison - cant choose other locations
* Use **arrow keys** to browse and **enter** to confirm

***

## Testing Delete Character

* Click on a character and click delete button
* A confirmation popup will appear
* Delete can be set to admin-only on config (default is admin only)

***

## Admin Commands

* `/charslots add license:xxxxx 2` - add 2 extra character slots to a player (license or citizen id)
* `/charslots remove license:xxxxx` - remove extra slots from a player (license or citizen id)
* `/charslots view` - see all players with extra slots (shows in server console)
* `/logout` - go back to character selection (admin only)
* `/deletechar citizenid` - force delete any character (god only, useful for corrupted characters)

{% hint style="warning" %}
These are admin/testing commands and only work with proper permissions. who counts as a multichar admin can be set in game from the admin menu (Staff > Roles).
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Cinematic camera animation, orbit speed, zoom, shake and all camera settings are fully configurable on our config. max name length, blacklisted words, default slots and nationality list are all configurable. character selection screen shows server name and logo. You can change them once you get the package. We will guide you :)
{% endhint %}

{% hint style="success" %}
Starter items, starter licenses and whether new characters also get the physical license card are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.

Add or edit spawn points in-game with the Multicharacter creator. the order in that list is the order on the spawn screen.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-properties/" %}
[meteo-properties](../meteo-properties/)
{% endcontent-ref %}
