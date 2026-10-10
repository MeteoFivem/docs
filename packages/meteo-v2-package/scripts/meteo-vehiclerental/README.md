---
description: >-
  Meteo vehicle rental - 7 rental locations including boats, built and edited
  in game with the rental creator, designed exclusively for the Meteo V2
  package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-vehiclerental/
---

# Meteo Vehicle Rental

This is a guide about testing the Meteo V2 vehicle rental script designed exclusively for the Meteo V2 package.

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

## Testing Vehicle Rentals

{% stepper %}
{% step %}
#### Go to a rental location
{% endstep %}

{% step %}
All locations are with blips on the map. You can see them on the map. Or teleport directly: `/tp -845.1431, -758.7166, 22.3279` to go to Revin' Rentals.
{% endstep %}

{% step %}
#### Talk to the clerk
{% endstep %}

{% step %}
Use your target on the clerk and pick **Talk to Clerk**. A dialogue opens where you can rent a vehicle or bring one back.
{% endstep %}

{% step %}
#### Browse the fleet
{% endstep %}

{% step %}
Pick **I'd like to rent a vehicle** to see the fleet. Every vehicle shows its picture, the deposit, the rental payment and the total you pay.
{% endstep %}

{% step %}
#### Rent a vehicle
{% endstep %}

{% step %}
Select a vehicle. The total is taken from your cash first and then from your bank. The vehicle is parked on the nearest free bay out front, the keys are in it and the clerk tells you the plate.
{% endstep %}

{% step %}
#### Rental papers
{% endstep %}

{% step %}
You also get `rentalpapers` with the plate, vehicle and deposit on it. Use them from your inventory to show them as a card to players standing next to you.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If every bay is taken by another vehicle you get "No available parking space". Move the car out of a bay and try again.
{% endhint %}

### Rental Locations

There are 7 locations on a fresh install:

* **Revin' Rentals** - main city (14 vehicles from $50 to $750)
* **Airport Rentals** - at the airport (5 vehicles)
* **Chromer Rentals** - up north paleto area (5 vehicles)
* **Boat Rentals** - 4 locations along the coast (seashark, dinghy, speeder)

### Returning Vehicle

{% stepper %}
{% step %}
#### Park it at the rental location
{% endstep %}

{% step %}
Drive the vehicle back to the location you rented it from and park it on one of the bays. Stop and get out of it.
{% endstep %}

{% step %}
#### Talk to the clerk
{% endstep %}

{% step %}
Pick **I'm bringing one back**. This option only shows when you have a rental out from that location, with a count next to it.
{% endstep %}

{% step %}
#### Return the vehicle
{% endstep %}

{% step %}
Every rental you have out is listed. If it can be returned it shows the deposit you get back. If not, the row tells you why - not parked on a bay, someone still in it, too damaged or destroyed. Pick it and your deposit comes back as cash. The rental payment is not refunded.
{% endstep %}

{% step %}
#### Too damaged or destroyed?
{% endstep %}

{% step %}
A badly damaged vehicle has to be repaired before the clerk takes it back. If the vehicle is destroyed or gone you lose the deposit - just like real life.
{% endstep %}
{% endstepper %}

***

## Rental Creator (Admin)

Rental locations are not in the config anymore. Admins build and edit them in game from the admin menu, and every save goes live for all players straight away without a restart.

{% stepper %}
{% step %}
#### Open the creator
{% endstep %}

{% step %}
Open the admin menu with **F9** or `/admin`, go to **Script Settings** and pick **Vehicle Rentals**. You see every rental location with its vehicle and bay count.
{% endstep %}

{% step %}
#### Basics
{% endstep %}

{% step %}
Create a new rental and give it a name. Pick the clerk ped model and an optional idle scenario.
{% endstep %}

{% step %}
#### Locations
{% endstep %}

{% step %}
Place the clerk where they should stand, then place the parking bays (up to 20). Rented vehicles appear on the nearest free bay and are returned on any of them.
{% endstep %}

{% step %}
#### Fleet
{% endstep %}

{% step %}
Add the vehicles players can rent (up to 30) with model, name, make, deposit and rental payment. You can also set an image URL. Leave it empty and the picture comes from the in-game image studio you open from [meteo-manage](../meteo-manage/).
{% endstep %}

{% step %}
#### Map blip
{% endstep %}

{% step %}
Turn the blip on or off and set its icon, colour and size. Save and the location is live.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Building and changing records is god tier in the admin menu. You can also duplicate, switch off, delete or teleport to a rental from the list, and export your rentals as a preset to share or import on another server.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Add or edit rental locations in-game with the Vehicle Rentals creator in the admin menu ([meteo-manage](../meteo-manage/)) - clerk, parking bays, vehicles, deposits, prices and blip. No code editing needed, and your changes survive script updates.
{% endhint %}

> This rental script is optimized for our crime system sea hunt locations and also apartment locations so players can easily get rental and drive around city when they come first.

* rentals stay active if you disconnect, so you can still return the vehicle later
* if an admin deletes a rental location, vehicles rented there can be returned at any other location
