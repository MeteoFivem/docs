---
description: >-
  Meteo bennys - vehicle customization script with in-game built locations
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-bennys/
---

# Meteo Bennys

<figure><img src="../../../../.gitbook/assets/meteo_bennys_01.webp" alt="Meteo Bennys customization menu"><figcaption><p>Meteo Bennys customization menu</p></figcaption></figure>

This is a guide about testing the Meteo V2 vehicle customization (bennys) script designed exclusively for the Meteo V2 package.

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

## Testing Bennys

### Basic Customization

{% stepper %}
{% step %}
#### Go to a bennys location
{% endstep %}

{% step %}
This is made for helicopters, boats and also vehicles. Lets go check Sandy Bennys for cars `/tp 1697.90, 3706.93, 33.52`. Helicopters and boats go to Higgins Bennys.
{% endstep %}

{% step %}
#### Spawn a vehicle
{% endstep %}

{% step %}
`/car adder` or spawn any vehicle.
{% endstep %}

{% step %}
#### Open customization menu
{% endstep %}

{% step %}
Drive into the bennys area, stay in the driver seat and press `E`. This is public and anyone can get customizations but if a mechanic is online then you must place an order instead.
{% endstep %}

{% step %}
#### Preview and buy
{% endstep %}

{% step %}
Pick parts and colors, they preview live on your vehicle. Drag to orbit the camera and scroll to zoom. Add what you like to the cart and pay from bank or cash. If you leave without paying your vehicle goes back to how it was.
{% endstep %}
{% endstepper %}

> If you don't want the mechanic requirement, it can be turned off in the config once you get the package. We will guide you.

### Bennys Locations

* **Sandy Bennys** - `/tp 1697.90, 3706.93, 33.52` (at Sandy Customs)
* **Higgins Bennys** - `/tp -744.41, -1467.88, 5.39` (helicopters and boats)

### Customization Options

* Performance mods (engine, brakes, transmission, suspension, armor, turbo)
* Cosmetic mods (spoiler, bumpers, skirts, exhaust, hood, fender, roof and more)
* Liveries, including addon vehicle liveries
* Interior parts and interior color
* Respray (primary, secondary, pearlescent and more, with a palette, custom colors and hex input)
* Wheels and tires
* Xenon lights, neon and tire smoke colors
* Window tint and horns (you can play a horn before buying)
* Extras and repair

### Repair

{% stepper %}
{% step %}
Damage your vehicle a bit and drive into a bennys location
{% endstep %}

{% step %}
Open the menu and pick repair. Empty your cart first if you have anything in it
{% endstep %}

{% step %}
Confirm and your engine and body gets fixed. The menu closes when it is done
{% endstep %}
{% endstepper %}

### Mechanic Orders

{% hint style="warning" %}
Make sure to use `/setjob yourid mechanic 4` to test mechanic orders - note this command is only available on our showcase server.
{% endhint %}

* Try placing order and see its giving the `meteo_mechreceipt` item to you
* After that for more info check out the mechanic job testing guide

{% content-ref url="../meteo-mechanicjob/" %}
[meteo-mechanicjob](../meteo-mechanicjob/)
{% endcontent-ref %}

### Building Bennys Locations (Admins)

{% stepper %}
{% step %}
Open the admin menu and go to Script Settings > Creator > Benny's
{% endstep %}

{% step %}
Add a new location, give it a name, pick the mechanic job that gets orders placed there and choose if it shows on the map
{% endstep %}

{% step %}
Aim at the middle of the garage floor to place the drive-in area and scroll to size the circle
{% endstep %}

{% step %}
Save it and it is live for everyone right away, no restart needed
{% endstep %}
{% endstepper %}

* Perk XP for purchases and repairs can also be changed in game from Script Settings > Benny's

***

## Good to Know

{% hint style="success" %}
Perk XP rewards are editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)), and you can add or edit Bennys locations (name, area, blip and the mechanic shop that gets the orders) in-game with the Benny's creator - no code editing needed, and your changes survive script updates. Script Settings is god tier only. Mod prices, order fees, tax and the mechanic requirement still live in the config. We will guide you :)
{% endhint %}
