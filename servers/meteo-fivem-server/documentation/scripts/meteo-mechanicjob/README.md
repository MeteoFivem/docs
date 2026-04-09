---
description: >-
  Meteo mechanic job - mechanic orders, parts and billing script designed
  exclusively for the meteo fivem server.
---

# Meteo Mechanic Job

This is a guide about testing the meteo fivem mechanic job script designed exclusively for meteo server.

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
Set mechanic job: `/setjob yourid mechanic 4` Get mechanic tablet: `/giveitem yourid meteo_mechanictablet 1`
{% endhint %}

***

## Mechanic Locations

* **duty station** - `/tp -349.7882, -139.0741, 39.4345` go here and toggle on duty first
* **bennys (customization)** - `/tp -339.1817, -116.6346, 39.0333` this is where customers place orders and where mechanics get parts
* **mechanic shop** - `/tp -326.7460, -140.0022, 39.4344, 253.2639` players can get mechanic tablet from here
* **work point** - `/tp -337.1071, -135.6217, 38.3523` this is where you connect vehicles and install parts
* **billing ped** - `/tp -330.8061, -129.4883, 39.0244` customers pay their invoices here. Money goes to mechanic society account
* **mechanic garage** - `/tp -357.3882, -107.5540, 38.6973` go here to get mechanic vehicles. For more info check out [meteo-jobgarage](../meteo-jobgarage/)
* **clothing locker** - `/tp -322.9909, -144.9560, 39.4344` go here to change into mechanic uniform. For more info check out [meteo-appearance](../meteo-appearance/)
* **boss menu** - `/tp -324.3511, -130.1849, 43.9199` go here to access boss menu (make sure you have grade 4). For more info check out [meteo-bossmenuv2](../meteo-bossmenuv2/)

***

## Testing Mechanic Job

### Placing an Order (As Customer)

{% stepper %}
{% step %}
Spawn any vehicle. Lets spawn `/car meteofivem`
{% endstep %}

{% step %}
Go to bennys `/tp -339.1817, -116.6346, 39.0333` and open it
{% endstep %}

{% step %}
Customize the vehicle and place the order. Place order is only available when a mechanic is on duty
{% endstep %}

{% step %}
It will give you a mechanic receipt item
{% endstep %}

{% step %}
Also check out [meteo-bennys](../meteo-bennys/) testing guide for more info about bennys
{% endstep %}
{% endstepper %}

### Doing the Work (As Mechanic)

{% stepper %}
{% step %}
Since you are already mechanic just use the mechanic receipt item
{% endstep %}

{% step %}
You can see the pending order on your mechanic tablet
{% endstep %}

{% step %}
Go to work point `/tp -337.1071, -135.6217, 38.3523`
{% endstep %}

{% step %}
Connect the vehicle and start installing parts
{% endstep %}

{% step %}
Mechanic can get parts from bennys `/tp -327.0645, -140.4799, 39.4345, 232.6171`
{% endstep %}

{% step %}
You can also install nitrous from there too
{% endstep %}

{% step %}
Finally disconnect the vehicle and send bill to the customer
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
Go to billing ped `/tp -330.8061, -129.4883, 39.0244` and pay the bill
{% endstep %}

{% step %}
This money will go to the society account of the mechanic
{% endstep %}

{% step %}
You can check that from boss menu `/tp -324.3511, -130.1849, 43.9199` and see the logs
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All mechanic locations, parts, prices, work points and billing settings are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-bennys/" %}
[meteo-bennys](../meteo-bennys/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-bossmenuv2/" %}
[meteo-bossmenuv2](../meteo-bossmenuv2/)
{% endcontent-ref %}
