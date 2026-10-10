---
description: >-
  Meteo properties - houses, MLOs and apartment complexes with in-game creator,
  realtors, security and break-ins script designed exclusively for the Meteo V2
  package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-properties/
    - servers/meteo-fivem-server/documentation/scripts/meteo-apartments/
    - packages/meteo-v2-package/scripts/meteo-apartments/
---

# Meteo Properties

This is a guide about testing the Meteo V2 properties script with in-game creator designed exclusively for the Meteo V2 package. Apartments are part of this script now too, so houses, MLOs and apartment complexes all live in one place.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

{% hint style="warning" %}
If you don't know how to get money use `/setmoney yourid bank 100000` to get money. This is a testing command and only works on our showcase server.
{% endhint %}

***

## Testing Properties

{% stepper %}
{% step %}
**Finding a Property**

Open the Properties app on [meteo-phone](../meteo-phone/) and go to Explore. You can see every property for sale on a list or a map, filter by price, area and garage, and set a waypoint. Properties for sale also show as blips on the map when you are nearby
{% endstep %}

{% step %}
**Buying a Property**

Go to the property door and point target to View listing. You can see the price, security level, member slots, storage and if it has a garage. Pay with bank or cash and you get the keys right away. Some properties are realtor only, then you need a realtor to sell it to you
{% endstep %}

{% step %}
**Creating a Property**

Use `/properties` to open the property admin panel and go to Create property. The creator walks you step by step through the basics (name, type, price, pictures), the interior, the location, and for MLOs the zone and the real doors you want to lock. Shells are for unlimited houses with a teleport inside, MLOs you can walk into without teleporting. The admin panel also has a dashboard, a property browser with search and filters, property types, apartment complexes and logs

{% hint style="warning" %}
`/properties` is an admin command and only works with proper permissions.
{% endhint %}
{% endstep %}

{% step %}
**Furnishing**

Go inside your property and use the F1 radial menu to open Furnish. Furnish the property as you want - up to 150 furniture items per property (configurable). Storage and wardrobe furniture work as your stash and outfits. Check [meteo-furnishing](../meteo-furnishing/) for more
{% endstep %}

{% step %}
**Managing Property**

Point target at the door or use Manage property in the F1 radial menu. From here you can lock and unlock, turn the doorbell on or off and:

* **Members** - add players standing next to you and give them a key
* **Roles** - make your own roles with their own color and permissions (door, garage, stash, wardrobe, furnish, upgrades, managing members and more). Manager, Key Holder and Guest are made for you to start with
* **Upgrades** - buy security levels, more member slots and more storage
* **Logs** - see who did what at your property

You can also lock and unlock and see security alerts from the Properties app on your phone
{% endstep %}

{% step %}
**Security System**

Properties have 6 security levels you can upgrade. Each level adds something:

* Level 1 (Basic) - free
* Level 2 (Smart Lock, $1,500) - auto-lock and phone alerts
* Level 3 (Reinforced, $4,000) - faster auto-lock and an alert when someone starts picking your lock
* Level 4 (Alarm System, $8,000) - burglar alarm
* Level 5 (Monitored, $15,000) - police alerts and remote locking
* Level 6 (Fortress, $30,000) - can't be lockpicked and blocks police raids
{% endstep %}

{% step %}
**Doorbell and Garage**

Players without a key can ring the doorbell. You hear it inside or get it on your phone when you are away. Properties with a garage spot use [meteo-garages](../meteo-garages/) to store your vehicles
{% endstep %}

{% step %}
**Real Estate Job**

Set your job to realestate: `/setjob yourid realestate 4` and go on duty. Realtors can unlock listed properties for tours, send buy offers to players from the Realtor tab in the phone Properties app and get a commission on each sale

{% hint style="warning" %}
`/setjob` is a testing command and only works on our showcase server.
{% endhint %}
{% endstep %}

{% step %}
**Selling Your Property**

Owners can sell their property to another player or sell it back to the city for 50% of the price (configurable)
{% endstep %}

{% step %}
**Lockpicking and Police Raid**

To test lockpicking spawn a `lockpick` or `advancedlockpick` item and try to break in with the keymash minigame. Higher security levels are harder. At least 1 police needs to be on duty for break-ins (configurable). To test a police raid set your job to police grade 3+: `/setjob yourid police 3`, go on duty and spawn the `police_stormram` item

This is connected to [meteo-perks](../meteo-perks/). Break-ins, Homeowner and Tactical Entry perks make lockpicking, upgrades and raids easier
{% endstep %}
{% endstepper %}

***

## Testing Apartments

{% stepper %}
{% step %}
**WiWang Hotel**

We already have the WiWang Hotel created for you with 285 rooms over 20 floors, so you don't have to create them. Use `/tp -824.7368, -702.1234, 28.0600` to go there and talk to the reception ped
{% endstep %}

{% step %}
**Getting a Room**

New characters get one free starter room. If you don't have a room yet, reception gives you one for free. Otherwise you can take one for $35,000. You can let reception pick the next free room or pick the room yourself, and you can also take a free room right at its door. Max 3 rooms per player across all complexes (configurable)
{% endstep %}

{% step %}
**Using Your Room**

Take the elevator to your floor and go to your room door. Furnish it, add members and buy upgrades the same way as a property. Ask reception "Where is my room again?" to get it marked on your map
{% endstep %}

{% step %}
**Inactive Players**

Rooms of players who have not logged in for 14 days are closed so new players can get one. Their furniture and storage stay in the room. If they come back within 60 days they talk to reception and get the room back with everything still inside, after that the room is cleared and freed. Complexes can also be set to charge rent, if the rent is not paid the room gets closed the same way
{% endstep %}

{% step %}
**Adding Complexes**

Admins can add more apartment complexes from the property admin panel (Complexes). Create the complex with its reception ped, elevators and garage, then add the rooms one by one in the property creator
{% endstep %}
{% endstepper %}

***

## Export, Import and Presets

* Properties, complexes and rooms can be exported, imported and saved as presets from the admin panel, so you can move them between servers or share them

***

## Admin Commands

| Command | Who | What it does |
|---------|-----|-------------|
| `/properties` | Admin | Open the property admin panel |
| `/reloadproperties` | Anyone | Reload the property UI if it gets stuck |
| `/propstats` | God | Show property, room and preset counts |
| `/aptsweep` | God | Run the apartment rent and inactivity check now |
| `/aptexpire [room id] [purge]` | God | Close a room now as if the tenant went inactive. Add `purge` to clear it too |
| `/propdev` | God | Test tools for rooms and export files |

***

## Good to Know

{% hint style="success" %}
Properties, apartment complexes, rooms and property types are all created and edited in-game from the property admin panel (`/properties`, or the Properties page in **Script Settings** in the admin menu, [meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Security levels, upgrade prices, lockpick and raid settings, realtor commission, resale and apartment rent and inactivity settings are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-furnishing/" %}
[meteo-furnishing](../meteo-furnishing/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-garages/" %}
[meteo-garages](../meteo-garages/)
{% endcontent-ref %}
