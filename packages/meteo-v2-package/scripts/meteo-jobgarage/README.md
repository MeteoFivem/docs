---
description: >-
  Meteo job garage - job vehicle spawning with liveries, extras, grade
  restrictions, storage limits, live 3D preview, max mods and an in-game garage
  creator designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-jobgarage/
---

# Meteo Job Garage

This is a guide about testing the Meteo V2 job garage script designed exclusively for the Meteo V2 package. Job vehicle spawning with livery customization, extras toggle, grade restrictions, storage limits, live 3D vehicle preview, max mods toggle, auto-generated category filters and an in-game creator to build garages.

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
* Familiar with [getting started](../../getting-started.md) basics

***

## Setup

Set your job to police using `/setjob yourid police 4` (grade 4 gives full access to all vehicles). Go to a police garage location using `/tp -574.0596, -90.0103, 33.6111` for the Police Garage. Use your target on the garage prop (parking meter) and pick **Open Police Garage** to open the garage UI.

***

## Testing Job Garage

### Spawning a Vehicle

{% stepper %}
{% step %}
**Browse vehicles**

The garage opens with a live 3D preview of the vehicle and a strip of vehicle cards at the bottom. Use the **Left/Right** arrows to move through them and the preview follows the selected vehicle. Switch category with **Q/E** (patrol, pursuit, special etc.) or press **/** to search by name. Categories are auto generated based on what vehicles are in that garage.
{% endstep %}

{% step %}
**Check vehicle cards**

Each vehicle shows the name, how many are in stock and the grade it needs. Vehicles you don't have the grade for show as locked, and vehicles with none left show "None left".
{% endstep %}

{% step %}
**Look around**

Drag with the mouse to orbit the camera around the preview and scroll to zoom. Press **R** to reset the camera and **H** to hide the UI for a clean look.
{% endstep %}

{% step %}
**Take it out**

Press **Space** (or the take out button) to spawn the vehicle. Verify it spawns on a free bay with the correct plate prefix and you get the keys. Press **Esc** to go back or close the garage.
{% endstep %}
{% endstepper %}

### Liveries

{% stepper %}
{% step %}
**Open the options**

Press **Enter** on a vehicle to open its options. Some vehicles have multiple liveries (like Default, Sheriff, Highway). The livery options only show if the vehicle has liveries set up.
{% endstep %}

{% step %}
**Grade locked liveries**

Some liveries are grade locked - verify locked liveries cannot be selected.
{% endstep %}

{% step %}
**Preview livery**

Pick a livery and it updates live on the preview vehicle. Verify the spawned vehicle actually has the selected livery applied.
{% endstep %}
{% endstepper %}

### Extras

* Extras are things like lightbars, work lights, MDT, rambar etc.
* Toggle extras on/off in the vehicle options
* There is also a **Max Mods** option that applies maximum vehicle performance mods (engine, brakes, suspension, transmission, armor, turbo)
* Extras update live on the preview vehicle too
* Verify the spawned vehicle has the correct extras enabled/disabled

### Returning a Vehicle

* Drive the job vehicle back to the garage and stop on one of its bays
* As the driver you get a **Return Vehicle** prompt, press **E**
* The vehicle is locked, everyone is taken out and it is removed. The stock count goes back up
* A return zone is made at every bay of the garage, so you can return on any of them

### Shared Garages (Multi-Job)

A garage does not have to belong to one job. It can be opened by every job on its list, which is how you run a shared LEO garage without duplicating it.

{% stepper %}
{% step %}
**Any listed job can open it**

A garage with police and sheriff on its job list opens for both. Anyone whose job is not on the list does not see the interaction at all.
{% endstep %}

{% step %}
**Vehicles can still be locked to one job**

Inside a shared garage a vehicle can be restricted to one of the garage's jobs. Sheriff opens the same garage but does not see the police-only units.
{% endstep %}

{% step %}
**Leave it off to share everything**

A vehicle with no restriction is available to every job that can open the garage.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Grade requirements still apply on top of this. A vehicle can be police-only **and** grade 3+, and both checks have to pass. Garages are for jobs only, gangs cannot be added to a garage.
{% endhint %}

To test it, add a second job to a garage in the creator, then set yourself to a job on the list and then to one that is not, and check the interaction and the vehicle list change.

### Multiple Spawn Points

* A garage can have a list of bays instead of just one
* On spawn the first bay with nothing blocking it is used, so vehicles do not stack on top of each other
* Spawn several vehicles in a row from a busy garage and watch them fill the bays one by one
* If every bay is blocked you get a notification to clear one first

***

## Garage Creator (Admin)

Job garages are not in the config anymore. Admins build and edit them in game from the admin menu, and every save goes live for all players straight away without a restart.

{% stepper %}
{% step %}
**Open the creator**

Open the admin menu with **F9** or `/admin`, go to **Script Settings** and pick **Job Garages**. You see every garage with its vehicle and bay count.
{% endstep %}

{% step %}
**Basics**

Create a new garage, give it a name and an optional plate prefix of up to 8 characters (like LSPD).
{% endstep %}

{% step %}
**Who can use it**

Add one row per job that can open the garage. The jobs are picked from a list your core has, so a garage can't point at a job that does not exist.
{% endstep %}

{% step %}
**Fleet**

Add the vehicles (up to 40) with name, model, category, minimum grade, stock count, fuel, dirt, warp into vehicle and an optional job restriction. Each vehicle row has its own liveries and extras with their own grade locks. You can also fill a row from the vehicle you are sitting in.
{% endstep %}

{% step %}
**Where it stands**

Place the parking meter (mouse wheel turns it), place the spawn bays (up to 12) and optionally the preview spot. Without a preview spot the first bay is used. Save and the garage is live.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Building and changing records is god tier in the admin menu. You can also duplicate, switch off, delete or teleport to a garage from the list, and export your garages as a preset to share or import on another server.
{% endhint %}

* Editing a garage live keeps the stock counts right, vehicles already out are counted back instead of handed out twice
* Deleting a garage with vehicles still out drops them from tracking, they can't be returned anymore and despawn on their own
* The server console warns about any garage whose job no longer exists in the core

***

## Validation Testing

These are important edge cases to check:

### Grade Restrictions

* Set your job grade to 1 with `/setjob yourid police 1`
* Verify you cannot take out vehicles that need a higher grade
* Verify grade locked liveries cannot be picked
* Verify the grade badge shows correctly on each vehicle card

### Storage Limits

* Take out all units of one vehicle until it shows none left
* Verify you cannot spawn more when the stock is at 0
* Return one vehicle and verify the stock goes back up by one
* Verify you can spawn again after returning

### Vehicle State

* Spawn a vehicle with a specific livery and extras selected
* Verify the spawned vehicle has the correct livery (not default)
* Verify the spawned vehicle has the correct extras toggled
* Verify max mods are applied when Max Mods was on
* Verify fuel level and dirt level match what is set for that vehicle

### UI State

* Open the garage, open a vehicle's options, then press **Esc** to go back and **Esc** again to close
* Verify the preview vehicle is deleted when the garage closes
* Move to a different vehicle and verify the old preview is replaced with the new one

***

## Testing Other Job Garages

Try different jobs to check their garages too:

* **Police Garage** - `/setjob yourid police 4` then `/tp -574.0596, -90.0103, 33.6111`
* **BCSO Police Garage** - police job, `/tp 1046.92, 2742.99, 38.67`
* **Police Air Unit** - police job, `/tp -584.59, -137.77, 52.0`
* **Police Boat Unit** - police job, `/tp -798.18, -1513.77, 1.6`
* **EMS Garage** - `/setjob yourid ambulance 4` then `/tp 68.47, -420.48, 39.34`
* **EMS Air Rescue** - ambulance job, `/tp 30.19, -434.74, 39.34`
* **BC EMS Garage** - ambulance job, `/tp 1093.97, 2741.28, 38.67`
* **Mechanic Garage** - `/setjob yourid mechanic 4` then `/tp -357.39, -107.55, 38.7`

Each job garage has its own set of vehicles, categories, liveries and extras.

{% hint style="info" %}
`/setjob` and `/tp` are admin commands.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Add or edit job garages in-game with the Job Garages creator in the admin menu ([meteo-manage](../meteo-manage/)) - locations, job access, vehicles, liveries, extras, grade requirements, storage counts and spawn points. No code editing needed, and your changes survive script updates.
{% endhint %}

* Custom plate prefix per garage (like LSPD431, EMS042 etc.)
* Vehicle fuel level and dirt level on spawn are set per vehicle
* Vehicles with no liveries or extras will not show empty options
* Categories are auto generated from the vehicles - just set the category and it shows up as a filter
* Vehicle pictures come from the in-game image studio you open from [meteo-manage](../meteo-manage/)
* Every vehicle a job garage hands out registers itself with [meteo-vehiclekeys](../meteo-vehiclekeys/) for shared keys, so any on-duty colleague can drive it without anyone passing keys around

**Connected scripts:**

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/)
{% endcontent-ref %}

{% content-ref url="../meteo-mechanicjob/" %}
[meteo-mechanicjob](../meteo-mechanicjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-vehiclekeys/" %}
[meteo-vehiclekeys](../meteo-vehiclekeys/)
{% endcontent-ref %}
