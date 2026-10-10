---
description: >-
  Meteo police radar - speed radar with bolo plates script designed exclusively
  for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-policeradar/
---

# Meteo Police Radar

This is a guide about testing the Meteo V2 police radar script designed exclusively for the Meteo V2 package.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Police job: `/setjob yourid police 4`

***

## Testing Police Radar

### Setup

{% stepper %}
{% step %}
Use `/tp -574.0596, -90.0103, 33.6111` to teleport to police garage and get a police vehicle
{% endstep %}

{% step %}
Get in vehicle - radar works in emergency vehicles (class 18) and configurable unmarked vehicles
{% endstep %}
{% endstepper %}

### Controls

* Use **arrow left** key to start/stop radar
* Use **arrow right** to lock/unlock current plate
* Use **arrow up** to cycle through radar modes
* Use **arrow down** to reset fast speeds
* Radar has front range of 50m and rear range of 50m
* Use `/radarpos` to drag the radar anywhere on your screen. Save keeps the position for next time and Reset puts it back

### Bolo Plates

{% stepper %}
{% step %}
Open the [police MDT](../meteo-mdt/) (**F5** by default) and add a new vehicle bolo with the plate
{% endstep %}

{% step %}
Police radar will alarm when that plate is found on the road. Plates flagged as stolen in the MDT are picked up too
{% endstep %}

{% step %}
Bolo check runs automatically when radar is on
{% endstep %}
{% endstepper %}

### Things to Check

* Radar starts and stops properly with arrow left
* Speed readings show up for nearby vehicles
* Plates lock correctly with arrow right
* Fast speeds above 85 mph/kmh get locked automatically and anything above 100 shows a red alert with sound (configurable)
* Bolo and stolen plate alerts work when a flagged vehicle passes by
* Radar position moves and saves with `/radarpos`
* Speed unit shows correctly (mph or kmh - configurable)

***

## Good to Know

{% hint style="success" %}
The jobs that get MDT bolo and stolen plate alerts are editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

{% hint style="info" %}
Speed unit (mph/kmh), alert speeds, ranges, bolo settings and allowed vehicles are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}
