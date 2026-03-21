---
description: >-
  Meteo police radar - speed radar with bolo plates script
  designed exclusively for the meteo fivem server.
---

# Meteo Police Radar

This is a guide about testing the meteo fivem police radar script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
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

### Bolo Plates

{% stepper %}
{% step %}
Open police MDT using **Y** keybind and add a new bolo plate
{% endstep %}

{% step %}
Police radar will alarm when that plate is found on the road
{% endstep %}

{% step %}
Bolo check runs automatically when radar is on
{% endstep %}
{% endstepper %}

### Things to Check

* Radar starts and stops properly with arrow left
* Speed readings show up for nearby vehicles
* Plates lock correctly with arrow right
* Fast speed alert triggers above 85 mph/kmh (configurable)
* Bolo plate alerts work when a flagged vehicle passes by
* Speed unit shows correctly (mph or kmh - configurable)

***

## Good to Know

{% hint style="success" %}
Speed unit (mph/kmh), alert speeds, ranges, bolo settings and allowed vehicles are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}
