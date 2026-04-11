---
description: >-
  Meteo job garage - job vehicle spawning with liveries, extras, grade
  restrictions, storage limits, 3D preview and max mods designed exclusively
  for the meteo fivem server.
---

# Meteo Job Garage

This is a guide about testing the meteo fivem job garage script designed exclusively for meteo server. job vehicle spawning with livery customization, extras toggle, grade restrictions, storage limits, live 3D vehicle preview, max mods toggle and auto-generated category filters.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-jobgarage-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Setup

set your job to police using `/setjob yourid police 4` (grade 4 gives full access to all vehicles). go to a police garage location using `/tp -574.0596, -90.0103, 33.6111` for LS Police Department garage. look at the garage prop (parking meter) and press **E** to open the garage UI

***

## Testing Job Garage

### Spawning a Vehicle

{% stepper %}
{% step %}
**Browse vehicles**

open the garage and browse vehicles. you can search by name or filter by category (patrol, pursuit, special, unmarked etc.). categories are auto generated based on what vehicles are in that garage
{% endstep %}

{% step %}
**Check vehicle cards**

each vehicle card shows the name, storage count (how many available) and grade requirement. vehicles you dont have the grade for will show as locked
{% endstep %}

{% step %}
**Spawn the vehicle**

click on a vehicle to select it and click spawn vehicle button. verify the vehicle spawns at the correct spawn point with the correct plate prefix
{% endstep %}
{% endstepper %}

### Liveries

{% stepper %}
{% step %}
**Select livery**

some vehicles have multiple liveries (like default, highway, city, SWAT). after selecting a vehicle the customization panel shows livery options (only if the vehicle has liveries configured)
{% endstep %}

{% step %}
**Grade locked liveries**

some liveries are grade locked - verify locked liveries cannot be selected
{% endstep %}

{% step %}
**Preview livery**

click on a livery to change it. you can preview the livery before spawning using view vehicle button. verify the spawned vehicle actually has the selected livery applied
{% endstep %}
{% endstepper %}

### Extras

* extras are things like lightbars, work lights, MDT, rambar etc.
* toggle extras on/off in the customization panel
* there is also a max mods toggle that applies maximum vehicle performance mods (engine, brakes, suspension, transmission, armor, turbo)
* extras update live in preview mode too
* verify the spawned vehicle has the correct extras enabled/disabled

### Vehicle Preview

* click view vehicle button to preview the vehicle in 3D before spawning
* you can change livery and extras while previewing and see them update live on the preview vehicle
* selecting a different vehicle while in preview mode automatically swaps to the new vehicle with its default livery and extras
* press **Backspace** to exit preview mode

### Returning a Vehicle

* get in the job vehicle and drive back to the garage location
* look at the garage prop and press **E**, then select return vehicle
* vehicle will be deleted and storage count goes back up

***

## Validation Testing

these are important edge cases to check:

### Grade Restrictions

* set your job grade to 1 with `/setjob yourid police 1`
* verify you cannot select vehicles that require grade 2+ (like interceptor)
* verify grade locked liveries cannot be clicked
* verify the grade badge shows correctly on each vehicle card

### Storage Limits

* spawn all available units of one vehicle type until storage shows 0/X
* verify you cannot spawn more when storage is at 0
* return one vehicle and verify storage goes back to 1/X
* verify you can spawn again after returning

### Vehicle State

* spawn a vehicle with specific livery and extras selected
* verify the spawned vehicle has the correct livery (not default)
* verify the spawned vehicle has the correct extras toggled
* verify max mods are applied when the max mods toggle was on
* verify fuel level and dirt level match the config values

### UI State

* open garage, select a vehicle, then press **Escape** to close
* reopen the garage and verify selection is reset (no vehicle selected, action buttons hidden)
* enter preview mode, press **Escape** to close - verify preview vehicle is deleted
* enter preview mode, select a different vehicle - verify old preview is replaced with new one

***

## Testing Other Job Garages

try different jobs to check their garages too:

* **Police** - `/setjob yourid police 4` then `/tp -574.0596, -90.0103, 33.6111`
* **EMS/Ambulance** - `/setjob yourid ambulance 4` (garage at pillbox medical)
* **Mechanic** - `/setjob yourid mechanic 4` (garage at hayes auto)
* **Police Air Unit** - police helicopter garage at mission row helipad
* **EMS Air Rescue** - medical helicopter at pillbox helipad

each job garage has its own set of vehicles, categories, liveries and extras

{% hint style="info" %}
`/setjob` and `/tp` are admin commands.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
all garage locations, vehicles, liveries, extras, grade requirements, storage counts and spawn points are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* custom plate prefix per garage (like LSPD001, EMS042 etc.)
* vehicle fuel level and dirt level on spawn are configurable too
* vehicles with no liveries or extras will not show empty customization panels
* categories are auto generated from vehicle configs - just set the category field and it shows up as a filter

**Connected scripts:**

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/) - police job with stations and features
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/) - EMS job with stations and features
{% endcontent-ref %}

{% content-ref url="../meteo-mechanicjob/" %}
[meteo-mechanicjob](../meteo-mechanicjob/) - mechanic job with stations and features
{% endcontent-ref %}
