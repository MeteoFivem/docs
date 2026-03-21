---
description: >-
  Meteo job garage - job vehicles with liveries and extras script
  designed exclusively for the meteo fivem server.
---

# Meteo Job Garage

This is a guide about testing the meteo fivem job garage script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Job Garage

### Spawning a Vehicle

* set your job to police using `/setjob yourid police 4` (grade 4 gives full access to all vehicles)
* go to a police garage location. use `/tp -574.0596, -90.0103, 33.6111` to go to LS Police Department garage
* interact with the garage prop (parking meter) to open the garage UI
* browse vehicles - you can search by name or filter by category (patrol, pursuit, special, unmarked etc.)
* each vehicle card shows the name, storage count (how many available) and grade requirement
* vehicles you dont have the grade for will show as locked
* click on a vehicle to select it and click spawn vehicle button

### Liveries

* some vehicles have multiple liveries (like default, sheriff, highway)
* after selecting a vehicle expand the customization panel to see livery options
* some liveries are grade locked too
* click on a livery to change it
* you can preview the livery before spawning using view vehicle button

### Extras

* extras are things like lightbars, work lights, toolbox etc.
* toggle extras on/off in the customization panel
* there is also a max mods toggle that applies maximum vehicle mods
* extras update live in preview mode too

### Vehicle Preview

* click view vehicle button to preview the vehicle in 3D before spawning
* you can change livery and extras while previewing and see them update live
* press **Backspace** to exit preview mode

### Returning a Vehicle

* get in the job vehicle and go back to the garage location
* interact with the garage prop and select return vehicle
* vehicle will be deleted and storage count goes back up

***

## Testing Other Job Garages

try different jobs to check their garages too:

* **Police** - `/setjob yourid police 4` then `/tp -574.0596, -90.0103, 33.6111`
* **EMS/Ambulance** - `/setjob yourid ambulance 4` (garage at pillbox medical)
* **Mechanic** - `/setjob yourid mechanic 4` (garage at hayes auto)
* **Police Air Unit** - police helicopter garage at mission row helipad
* **EMS Air Rescue** - medical helicopter at pillbox helipad
* **Police Boat Unit** - police boats at water dock

each job garage has its own set of vehicles, categories, liveries and extras

***

## Good to Know

* all garage locations, vehicles, liveries, extras, grade requirements, storage counts and spawn points are configurable on our config. you can change them once you get the server. we will guide you :)
* custom plate prefix per garage (like LSPD001, EMS042 etc.)
* vehicle fuel level and dirt level on spawn are configurable too
