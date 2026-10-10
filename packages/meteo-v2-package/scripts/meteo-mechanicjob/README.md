---
description: >-
  Meteo mechanic job - mechanic orders, parts, nitrous and billing script
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-mechanicjob/
---

# Meteo Mechanic Job

This is a guide about testing the Meteo V2 mechanic job script designed exclusively for the Meteo V2 package.

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

{% hint style="warning" %}
Set mechanic job: `/setjob yourid mechanic 4` Get mechanic tablet: `/giveitem yourid meteo_mechanictablet 1` - note these commands are only available on our showcase server.
{% endhint %}

***

## Mechanic Locations

* **duty station** - `/tp -349.7882, -139.0741, 39.4345` go here and toggle on duty first
* **bennys (customization)** - `/tp -339.1817, -116.6346, 39.0333` this is where customers place orders
* **mechanic shop** - `/tp -326.7460, -140.0022, 39.4344, 253.2639` mechanics can get the mechanic tablet, parts and nitrous from here
* **work point** - `/tp -337.1071, -135.6217, 38.3523` this is where you connect vehicles and install parts
* **billing ped** - `/tp -330.8061, -129.4883, 39.0244` customers pay their invoices here. Money goes to mechanic society account
* **mechanic garage** - `/tp -357.3882, -107.5540, 38.6973` go here to get mechanic vehicles. For more info check out [meteo-jobgarage](../meteo-jobgarage/)
* **clothing locker** - `/tp -322.9909, -144.9560, 39.4344` go here to change into mechanic uniform. For more info check out [meteo-appearance](../meteo-appearance/)
* **boss menu** - `/tp -324.3511, -130.1849, 43.9199` go here to access boss menu (make sure you have grade 4). For more info check out [meteo-bossmenu](../meteo-bossmenu/)

***

## Testing Mechanic Job

### Placing an Order (As Customer)

{% stepper %}
{% step %}
Spawn any vehicle. Lets spawn `/car adder`
{% endstep %}

{% step %}
Go to bennys `/tp -339.1817, -116.6346, 39.0333` and open it
{% endstep %}

{% step %}
Customize the vehicle and place the order. Place order is only available when a mechanic is on duty
{% endstep %}

{% step %}
It will give you a mechanic receipt item (`meteo_mechreceipt`)
{% endstep %}

{% step %}
Also check out [meteo-bennys](../meteo-bennys/) testing guide for more info about bennys
{% endstep %}
{% endstepper %}

### Doing the Work (As Mechanic)

{% stepper %}
{% step %}
Since you are already mechanic just use the mechanic receipt item. It creates a work order
{% endstep %}

{% step %}
Use the mechanic tablet and you can see the pending order there. Accept it
{% endstep %}

{% step %}
Go to work point `/tp -337.1071, -135.6217, 38.3523`
{% endstep %}

{% step %}
Sit in the vehicle, connect it to the order from the tablet and start installing parts
{% endstep %}

{% step %}
Each part needs its item. Mechanic can get parts from the mechanic shop `/tp -326.7460, -140.0022, 39.4344`

* `meteo_enginepart` - performance parts
* `meteo_bodypart` - cosmetic parts
* `meteo_respray` - respray
* `meteo_wheels` - wheels
* `meteo_wiring` - lights, tint and electronics
{% endstep %}

{% step %}
Performance parts have a small skill check before installing, so be careful
{% endstep %}

{% step %}
Finally disconnect the vehicle and send the bill to the customer from the invoices tab
{% endstep %}
{% endstepper %}

### Nitrous

{% stepper %}
{% step %}
Buy `nitrous` from the mechanic shop `/tp -326.7460, -140.0022, 39.4344`
{% endstep %}

{% step %}
Stand next to an empty vehicle and use the nitrous item. Pass the skill check to install it
{% endstep %}

{% step %}
Get in the driver seat and hold `Left Ctrl` to boost. Other players see the boost too
{% endstep %}

{% step %}
Use another nitrous item on the same vehicle to refill the tank
{% endstep %}
{% endstepper %}

### Billing and Payment

{% stepper %}
{% step %}
Since you are the customer too it will get to you
{% endstep %}

{% step %}
Meteo phone will get an email about the invoice
{% endstep %}

{% step %}
Go to billing ped `/tp -330.8061, -129.4883, 39.0244` and pay the bill with bank or cash
{% endstep %}

{% step %}
This money will go to the society account of the mechanic
{% endstep %}

{% step %}
You can check that from boss menu `/tp -324.3511, -130.1849, 43.9199` and see the logs
{% endstep %}
{% endstepper %}

### Building Mechanic Shops (Admins)

{% stepper %}
{% step %}
Open the admin menu and go to Script Settings > Creator > Mechanic Shops
{% endstep %}

{% step %}
Add a shop, pick its job and place the billing clerk, work points, duty spots and blip
{% endstep %}

{% step %}
Set the same job on the bennys locations you want to send orders to this shop. See [meteo-bennys](../meteo-bennys/)
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Add or edit mechanic shops (job, billing clerk, work points, duty spots and blip) in-game with the Mechanic Shops creator in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Parts, install times, nitrous and billing settings still live in the config. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-bennys/" %}
[meteo-bennys](../meteo-bennys/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-bossmenu/" %}
[meteo-bossmenu](../meteo-bossmenu/)
{% endcontent-ref %}
