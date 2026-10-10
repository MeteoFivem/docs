---
description: >-
  Meteo fuel - fuel, jerrycan and electric charging script for all vehicle types
  with an in-game station creator, designed exclusively for the Meteo V2
  package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-fuelv2/
    - packages/meteo-v2-package/scripts/meteo-fuelv2/
---

# Meteo Fuel

This is a guide about testing the Meteo V2 fuel script designed exclusively for the Meteo V2 package.

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

## Testing Fuel

### Refueling at Station

{% stepper %}
{% step %}
#### Spawn a vehicle
{% endstep %}

{% step %}
Spawn `/car adder` and make sure its fuel is low. Get in it and the nearest gas stations show on the map, then drive to one.
{% endstep %}

{% step %}
#### Refuel the vehicle
{% endstep %}

{% step %}
Get out, go near the pump, point your target at it and click on **Refuel Vehicle**. It shows the cost as it fills. You can stop it with backspace, or it stops on its own when the tank is full.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Refuel Vehicle only shows when the vehicle is close to the pump, nobody is in the driver seat and the tank is not already full.
{% endhint %}

### Jerrycan

{% stepper %}
{% step %}
#### Buy a jerrycan
{% endstep %}

{% step %}
Point your target at any pump and click on **Fuel Cans**. Pick **Buy Jerrycan** to get a full one.
{% endstep %}

{% step %}
#### Use it on a vehicle
{% endstep %}

{% step %}
Stand next to a vehicle and use the jerrycan from your inventory. Pick the jerrycan you want and it refuels the vehicle. Backspace stops it.
{% endstep %}

{% step %}
#### Refill the jerrycan
{% endstep %}

{% step %}
Go back to a pump, open **Fuel Cans** and pick **Refuel Jerrycan**. Open your inventory and check it is back to 100% after the refill.
{% endstep %}
{% endstepper %}

### Electric Vehicles

{% stepper %}
{% step %}
#### Spawn an electric vehicle
{% endstep %}

{% step %}
Now lets try an electric vehicle. Spawn `/car neon` and it shows the charging stations on the map instead of gas stations while you are in the vehicle.
{% endstep %}

{% step %}
#### Charge the vehicle
{% endstep %}

{% step %}
Go to a charging station, get out, point your target at the charger and click on **Charge Vehicle**. An electric vehicle can not use a gas pump and a normal vehicle can not use a charger.
{% endstep %}

{% step %}
#### Check the HUD
{% endstep %}

{% step %}
Get back in the vehicle and see the charge updated on the vehicle hud too.
{% endstep %}
{% endstepper %}

### Helicopters and Boats

* Fuel works for helicopters and boats too, they just burn it faster
* There are private pumps for them. Check them on `/tp -702.1304, -1453.2075, 5.0005` and `/tp -807.4984, -1497.2971, 1.5952`

***

## In-Game Creator

Gas stations, charging stations, private chargers and private pumps are not in the config anymore. Admins build them in game and they show up for everyone right away, nothing has to be restarted.

{% stepper %}
{% step %}
#### Open the creator
{% endstep %}

{% step %}
Open the [admin menu](../meteo-manage/) and go to **Script Settings > Creator > Fuel**.
{% endstep %}

{% step %}
#### Add a station
{% endstep %}

{% step %}
Add a new one and pick its type:

* **Gas station** - only a map marker, the pumps at real stations are already part of the map
* **Charging station** - a charger prop with a map marker
* **Private charger** - the same charger with nothing on the map
* **Private pump** - a pump prop with nothing on the map, good for a helipad or a yard
{% endstep %}

{% step %}
#### Place it
{% endstep %}

{% step %}
Give it a name, choose if it shows on the map and set a map label if you want one. Then place it where you are standing. While you aim a charger or a pump you see the real prop, and the mouse wheel turns it. Save and it is there for everyone.
{% endstep %}

{% step %}
#### Share it
{% endstep %}

{% step %}
Your stations can be exported, imported and saved as presets from the admin menu, so you can share a setup with another server.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
The creator is for admins only.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Add or edit gas stations, charging stations, private chargers and private pumps (location, prop and blip) in-game with the Fuel creator in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Fuel prices, consumption per vehicle class, charging speed and jerrycan settings still live in the config. We will guide you :)
{% endhint %}
