---
description: >-
  Meteo dealerships - owned and public dealership script with finance
  designed exclusively for the meteo fivem server.
---

# Meteo Dealerships

This is a guide about testing the meteo fivem dealership script designed exclusively for meteo server. There are 2 types of dealerships. Owned and public.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Owned Dealership

### Setup

{% stepper %}
### Teleport to the dealership

`/tp -72.8717, 83.0953, 71.7200` and teleport to the location.

### Import vehicles

If you trying first time it will not show vehicles on the showroom. Now use `/dealeradmin` command on the chat.

### Configure vehicles

Go to import vehicles and select Overwrite (delete all, re-import) and import. On there now you can see all vehicles. And also edit their prices, shops etc etc.
{% endstepper %}

{% hint style="warning" %}
Make sure to use `/dealeradmin` to import vehicles before testing - note this command is only available on our test server.
{% endhint %}

### Setting Owner

* Now go to dealerships tab. You can see the owned ones have set owner option. First set owner to yourself with your id (use `/id` if you dont know)
* Now you are the owner of the dealership

### Managing Dealership

* Its `/tp -67.6682, 78.2980, 71.7200` point target and open the manage menu
* There are lot of features that i cant write all of them here. Please check the exclusive video for that :)
* For the owner or with permissions player can deposit money into the dealership and order vehicles
* After placing the order you can see the vehicle on the Inventory tab. You can change its price for players and do test drives, sell, add as featured on the menu and also add limited time discounts
* All those limited time offers will show highlighted on the dealership vehicle browser
* As a owner or with permissions you can turn off and on the test drives and more customizations

### Finance System

* Our finance system is connected with garages and meteo phone. Player will get reminders to the phone

***

## Testing Public Dealership

{% stepper %}
### Go to the public dealership

Teleport using `/tp -30.3085, -1104.2148, 26.4785`.

### Browse and buy

Browse vehicles and buy vehicle you want. Maybe with the finance.

### Check test drives

Also test drives can be enabled or disabled on config of this public shops. Only owned ones can update ingame with owner or permission.
{% endstepper %}

### Other Dealership Locations

* **Marina Yacht Club** - `/tp -729.5516, -1319.5695` (boats)
* **Los Santos Air** - `/tp -1621.3098, -3152.8059` (aircraft)

***

## Good to Know

{% hint style="success" %}
All dealership locations, vehicle prices, finance settings (10% interest), test drive durations, employee grades and permissions are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

> Connected with garages, phone for finance reminders, and banking for payments.

{% content-ref url="../meteo-garages/" %}
[meteo-garages](../meteo-garages/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-banking/" %}
[meteo-banking](../meteo-banking/)
{% endcontent-ref %}
