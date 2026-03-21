---
description: >-
  Meteo mechanic job - mechanic orders, parts and billing script
  designed exclusively for the meteo fivem server.
---

# Meteo Mechanic Job

This is a guide about testing the meteo fivem mechanic job script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Mechanic job: `/setjob yourid mechanic 4`
* Mechanic tablet: `/giveitem yourid meteo_mechanictablet 1`

***

## Mechanic Locations

* **duty station** - `/tp -349.7882, -139.0741, 39.4345` go here and toggle on duty first
* **bennys (customization)** - `/tp -339.1817, -116.6346, 39.0333` this is where customers place orders and where mechanics get parts
* **mechanic shop** - `/tp -326.6155, -139.9312, 39` players can get mechanic tablet from here
* **work point** - `/tp -337.1071, -135.6217, 38.3523` this is where you connect vehicles and install parts
* **billing ped** - `/tp -330.8061, -129.4883, 39.0244` customers pay their invoices here. money goes to mechanic society account
* **mechanic garage** - `/tp -357.3882, -107.5540, 38.6973` go here to get mechanic vehicles. for more info check out [meteo-jobgarage](../meteo-jobgarage/)
* **clothing locker** - `/tp -322.9909, -144.9560, 39.4344` go here to change into mechanic uniform. for more info check out [meteo-appearance](../meteo-appearance/)
* **boss menu** - `/tp -324.3511, -130.1849, 43.9199` go here to access boss menu (make sure you have grade 4). for more info check out [meteo-bossmenuv2](../meteo-bossmenuv2/)

***

## Testing Mechanic Job

### Placing an Order (As Customer)

* spawn any vehicle. lets spawn `/car meteofivem`
* go to bennys `/tp -339.1817, -116.6346, 39.0333` and open it
* customize the vehicle and place the order. place order is only available when a mechanic is on duty
* it will give you a mechanic receipt item
* also check out [meteo-bennys](../meteo-bennys/) testing guide for more info about bennys

### Doing the Work (As Mechanic)

* since you are already mechanic just use the mechanic receipt item
* you can see the pending order on your mechanic tablet
* go to work point `/tp -337.1071, -135.6217, 38.3523`
* connect the vehicle and start installing parts
* mechanic can get parts from bennys `/tp -339.1817, -116.6346, 39.0333`
* you can also install nitrous from there too
* finally disconnect the vehicle and send bill to the customer

### Billing and Payment

* since you are the customer too it will get to you
* meteo phone will get an email about the invoice
* go to billing ped `/tp -330.8061, -129.4883, 39.0244` and pay the bill
* this money will go to the society account of the mechanic
* you can check that from boss menu `/tp -324.3511, -130.1849, 43.9199` and see the logs

***

## Good to Know

* all mechanic locations, parts, prices, work points and billing settings are configurable on our config. you can change them once you get the server. we will guide you :)
* connected with [meteo-bennys](../meteo-bennys/) for vehicle customization, [meteo-phone](../meteo-phone/) for invoice emails and [meteo-bossmenuv2](../meteo-bossmenuv2/) for society management
