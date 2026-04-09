---
description: >-
  Meteo garages - vehicle storage, depot and police impound script designed
  exclusively for the meteo fivem server.
---

# Meteo Garages

This is a guide about testing the meteo fivem advanced garages script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-testing-server.md).
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

Use `/tp 274.29, -334.15, 44.92` on chat and teleport to public garage location. spawn vehicle lets spawn `/car meteofivem`. then press e and try to store it. but you will get notify not owned vehicle. use `/admincar` and now try and it must store the vehicle. again press e to open the garage menu. on menu you can take out the vehicle. click take out and take out the vehicle and see

{% hint style="warning" %}
`/admincar` is only for admins. this is a testing command.
{% endhint %}
{% endstep %}

{% step %}
**Depot (Vehicle Recovery)**

Now drive off and use `/dv` to delete the vehicle. now go to `/tp 409.1124, -1622.9849, 29.2919`. this is depot. now you can get the vehicle again with paying a fee. these fees are configurable

{% hint style="warning" %}
`/dv` is for just testing purposes.
{% endhint %}
{% endstep %}

{% step %}
**Police Impound**

Now set your job to police `/setjob yourid police 4` and use `/impound` on chat. then you can give reason and impound the vehicle. now go to `/tp 371.4974, -1612.7997, 29.2919` (this is impound) and pay fees and take out the vehicle. also police can `/depot` the vehicle too

{% hint style="warning" %}
`/setjob` is a testing command and only works on our showcase server.
{% endhint %}
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All garage locations, depot fees, impound fees and settings are configurable on our config. you can change them once you get the server. we will guide you :). there are multiple garage locations around the map including car, air and sea garages.
{% endhint %}
