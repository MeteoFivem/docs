---
description: >-
  Meteo job garage - job vehicles with liveries and extras script
  designed exclusively for the meteo fivem server.
---

# Meteo Job Garage

This is a guide about testing the meteo fivem job garage script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Job Garage

### Spawning a Vehicle

{% stepper %}
### Set your job

Set your job to police using `/setjob yourid police 4` (grade 4 gives full access to all vehicles).

### Go to the garage

Go to a police garage location. Use `/tp -574.0596, -90.0103, 33.6111` to go to LS Police Department garage.

### Open the garage UI

Interact with the garage prop (parking meter) to open the garage UI. Browse vehicles - you can search by name or filter by category (patrol, pursuit, special, unmarked etc.).

### Check vehicle cards

Each vehicle card shows the name, storage count (how many available) and grade requirement. Vehicles you dont have the grade for will show as locked.

### Spawn the vehicle

Click on a vehicle to select it and click spawn vehicle button.
{% endstepper %}

{% hint style="warning" %}
Make sure to use `/setjob yourid police 4` before testing - note this command is only available on our test server.
{% endhint %}

### Liveries

* Some vehicles have multiple liveries (like default, sheriff, highway)
* After selecting a vehicle expand the customization panel to see livery options
* Some liveries are grade locked too
* Click on a livery to change it
* You can preview the livery before spawning using view vehicle button

### Extras

* Extras are things like lightbars, work lights, toolbox etc.
* Toggle extras on/off in the customization panel
* There is also a max mods toggle that applies maximum vehicle mods
* Extras update live in preview mode too

### Vehicle Preview

* Click view vehicle button to preview the vehicle in 3D before spawning
* You can change livery and extras while previewing and see them update live
* Press **Backspace** to exit preview mode

### Returning a Vehicle

{% stepper %}
### Drive back to the garage

Get in the job vehicle and go back to the garage location.

### Return the vehicle

Interact with the garage prop and select return vehicle. Vehicle will be deleted and storage count goes back up.
{% endstepper %}

***

## Testing Other Job Garages

Try different jobs to check their garages too:

* **Police** - `/setjob yourid police 4` then `/tp -574.0596, -90.0103, 33.6111`
* **EMS/Ambulance** - `/setjob yourid ambulance 4` (garage at pillbox medical)
* **Mechanic** - `/setjob yourid mechanic 4` (garage at hayes auto)
* **Police Air Unit** - police helicopter garage at mission row helipad
* **EMS Air Rescue** - medical helicopter at pillbox helipad
* **Police Boat Unit** - police boats at water dock

Each job garage has its own set of vehicles, categories, liveries and extras.

{% hint style="warning" %}
The `/setjob` and `/tp` commands are only available on our test server so you can quickly switch between jobs.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
All garage locations, vehicles, liveries, extras, grade requirements, storage counts and spawn points are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Custom plate prefix per garage (like LSPD001, EMS042 etc.)
* Vehicle fuel level and dirt level on spawn are configurable too
