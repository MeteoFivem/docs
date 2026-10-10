---
description: >-
  Meteo dealerships - owned and public dealership script with finance designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-dealerships/
---

# Meteo Dealerships

This is a guide about testing the Meteo V2 dealership script designed exclusively for the Meteo V2 package. There are 2 types of dealerships. Owned and public.

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

## Testing Owned Dealership

### Setup

{% stepper %}
{% step %}
#### Teleport to the dealership
{% endstep %}

{% step %}
`/tp -72.8717, 83.0953, 71.7200` and teleport to the location.
{% endstep %}

{% step %}
#### Import vehicles
{% endstep %}

{% step %}
If you are trying it for the first time it will not show vehicles on the showroom. Now use `/dealeradmin` command on the chat.
{% endstep %}

{% step %}
#### Configure vehicles
{% endstep %}

{% step %}
Go to the Vehicles tab, pick the Overwrite import mode (delete all, re-import) and import. Now you can see all vehicles there and also edit their prices, shops and more.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Make sure to use `/dealeradmin` to import vehicles before testing - note this command is only available on our showcase server.
{% endhint %}

### Setting Owner

* Now go to the Dealerships tab. You can see the owned ones have a set owner option. First set the owner to yourself with your id (use `/id` if you don't know it)
* Now you are the owner of the dealership

### Managing Dealership

* Use `/tp -67.6682, 78.2980, 71.7200`, target the point and open the manage menu
* You can also use `/dealermanage` while you are standing at a dealership you manage
* There are a lot of features so we can't write all of them here. Please check the exclusive video for that :)
* For the owner or with permissions player can deposit money into the dealership and order vehicles
* After placing the order you can see the vehicle on the Inventory tab. You can change its price for players and do test drives, sell, add as featured on the menu and also add limited time discounts
* All those limited time offers will show highlighted on the dealership vehicle browser
* As an owner or with permissions you can turn test drives on and off and do more customizations
* Employee roles and their permissions are built in game by each dealership owner on the Roles tab

### Finance System

* Our finance system is connected with garages and meteo phone. Players will get reminders on the phone

***

## Testing Dealership Creator

Every dealership is now built in game. No config edits needed.

{% stepper %}
{% step %}
#### Open the creator
{% endstep %}

{% step %}
Use `/dealeradmin` and go to the Creator tab.
{% endstep %}

{% step %}
#### Build a dealership
{% endstep %}

{% step %}
Go through the steps: Basics (name, owned or public, blip), Vehicles (categories and shops it sells), Locations (shop point, preview spot, spawn points, showroom slots, sell back point) and Extras (finance ped, test drives, job applications). You can capture positions right where you are standing.
{% endstep %}

{% step %}
#### Review and save
{% endstep %}

{% step %}
Check the Review step and save. The dealership shows up straight away without a restart.
{% endstep %}

{% step %}
#### Share it
{% endstep %}

{% step %}
You can export and import dealerships, and save presets on the server as a checkpoint before a big change.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Vehicle images in the browser come from meteo-imagestudio when it is running, so you can capture your own vehicle images in game.
{% endhint %}

***

## Testing Public Dealership

{% stepper %}
{% step %}
#### Go to the public dealership
{% endstep %}

{% step %}
Teleport using `/tp -30.3085, -1104.2148, 26.4785`.
{% endstep %}

{% step %}
#### Browse and buy
{% endstep %}

{% step %}
Browse vehicles and buy the vehicle you want. Maybe with the finance.
{% endstep %}

{% step %}
#### Check test drives
{% endstep %}

{% step %}
Test drives for public dealerships are enabled or disabled in the creator. Owned ones can also be updated in game by the owner or anyone with permission.
{% endstep %}
{% endstepper %}

### Other Dealership Locations

* **Marina Yacht Club** - `/tp -729.5516, -1319.5695` (boats)
* **Los Santos Air** - `/tp -1621.3098, -3152.8059` (aircraft)

***

## Good to Know

{% hint style="success" %}
Add or edit dealerships in-game with the dealership creator, and edit vehicle prices and shops on the Vehicles tab of `/dealeradmin` - you can also open the panel from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)). No code editing needed, and your changes survive script updates. Finance settings (10% interest), sell back and paychecks still live in the config. We will guide you :)
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
