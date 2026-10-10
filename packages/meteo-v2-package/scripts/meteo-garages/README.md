---
description: >-
  Meteo garages - vehicle storage, depot, police impound and tow job script
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-garages/
---

# Meteo Garages

This is a guide about testing the Meteo V2 advanced garages script designed exclusively for the Meteo V2 package. Garages, impound lots and depots are all built in game now, and police seizures can be sent to a tow job instead of the car just vanishing.

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

## Testing Garages

{% stepper %}
{% step %}
**Storing and Retrieving Vehicles**

Use `/tp 274.29, -334.15, 44.92` on chat and teleport to the public garage location. Spawn a vehicle with `/car adder`. Then press E and try to store it. You will get a notify that you don't own this vehicle. Use `/admincar` and try again, now it must store the vehicle. Press E again to open the garage menu. On the menu you can take out the vehicle. Click take out and see it come out on a free parking spot.

{% hint style="warning" %}
`/admincar` is only for admins. This is a testing command.
{% endhint %}
{% endstep %}

{% step %}
**Garage Menu**

On the garage menu you can search by name, brand or plate, filter by favourites, here or elsewhere, and favourite a vehicle. Each vehicle shows its mileage, fuel, engine and body. If a vehicle is parked at another garage you can transfer it to this one for a fee.
{% endstep %}

{% step %}
**Depot (Vehicle Recovery)**

Now drive off and use `/dv` to delete the vehicle. Now go to `/tp 409.1124, -1622.9849, 29.2919`. This is the depot. Talk to the depot attendant and you can get the vehicle back by paying a fee. These fees are configurable.

{% hint style="warning" %}
`/dv` is for just testing purposes.
{% endhint %}
{% endstep %}

{% step %}
**Police Impound**

Now set your job to police `/setjob yourid police 4`, stand next to the vehicle and use `/impound` on chat. Then you can give a reason and a release fee and impound the vehicle. Now go to `/tp 371.4974, -1612.7997, 29.2919` (this is the impound), talk to the impound clerk, pay the fee and take out the vehicle. Police can also use `/depot` to send a vehicle to the depot.

`/impound` and `/depot` only work for on duty police. If the tow job is enabled (it is by default), an owned vehicle is not removed right away. It waits for a tow truck instead, see the next section.

{% hint style="warning" %}
`/setjob` is a testing command and only works on our showcase server.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## Testing the Tow Job

When police use `/impound` or `/depot` on an owned vehicle, it stays where it is, locked, and a tow request goes out to the mechanic job. The tow driver loads it on a flatbed and drops it off at the impound lot or depot. Unowned cars, boats, aircraft and cars with someone inside are still removed instantly.

{% stepper %}
{% step %}
**Request a Tow**

Spawn a vehicle with `/car adder` and use `/admincar` so it is owned. Get out of it, set your job to police `/setjob yourid police 4` and use `/impound` or `/depot` next to it. You will get a notify that the tow is requested and the car stays there until a tower picks it up.
{% endstep %}

{% step %}
**Accept the Request**

Set your job to mechanic `/setjob yourid mechanic 4`. Open your phone and go to the **Tow** app. You will see the request on the board with the car and where it needs to go. Accept it and the route is set to the car.
{% endstep %}

{% step %}
**Load the Car**

Spawn a flatbed with `/car flatbed` and back it up close to the car. Get out, look at the car and use **Load onto flatbed**. The car is loaded and a route is set to the right lot.
{% endstep %}

{% step %}
**Drop It Off**

Drive to the impound lot or depot and park near the clerk. Get out, look at the flatbed and use **Drop off car**. You get paid to your bank and the car is now in the impound or depot for the owner to pay and collect.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If nobody takes the request in time, or the tower leaves, goes off duty or takes too long, the car is sent to the lot automatically so nothing gets stuck. The tower can also report the car missing from the Tow app if it is not at the spot.
{% endhint %}

***

## Testing the Garage Creator

Garages, impound lots and depots are no longer in the config. Admins build them in game and the change applies live with no restart.

{% stepper %}
{% step %}
**Open the Creator**

Open the admin menu with `/admin` and go to script settings, then the creator, then **Garages**.
{% endstep %}

{% step %}
**Add a Garage**

Add a new one and pick the type - garage, impound or depot - and the vehicle type it takes (cars, aircraft, boats or all). Give it a name.
{% endstep %}

{% step %}
**Place It**

For a garage, place the point where players press E and set how close they need to be. For an impound or depot, pick the clerk ped and place it. Then add the parking spots by sitting in a car on each spot and saving it.
{% endstep %}

{% step %}
**Save**

Choose if it shows on the map and save. It is live straight away. If you delete a garage, any cars parked there are moved to the depot for free so nobody loses a vehicle.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
The creator is part of the admin menu script settings, which is god tier only. You can also export, import and save your garages as presets to share them.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Add or edit garages, impound lots and depots (type, vehicle class, clerk ped, spawn points and blip) in-game with the Garages creator in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. There are multiple garage, impound and depot locations around the map already set up, including car, air and sea garages. Depot fees, transfer fees, tow pay and tow jobs still live in the config. We will guide you :)
{% endhint %}
