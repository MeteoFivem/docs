---
description: >-
  Meteo repo - vehicle repossession job, tow stolen vehicles back to impound, higher level repos mean more pay.
---

# Meteo Repo Job

Vehicle repossession job. Tow stolen vehicles back to impound. Higher level repos mean more dangerous situations and better pay.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-repojob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Repo Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to repo office location (or use `/tp 512.5959, -625.5834, 28.4790, 240.2101` for main dispatcher). Talk to the npc and pick up your tow truck. Get in the driver seat and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to repo job. Click "clock in" button. Make sure u are in tow truck driver seat (required). Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept repo task**

Server will dispatch a new repo target automatically. U will see the vehicle location, type (normal/highend/exotic), and pickup spot. Click "accept task" to start. GPS will route u to the vehicle location. Follow the gps marker.
{% endstep %}

{% step %}
**Locate the vehicle**

Drive to the marked repo location. When u get within 30m the repo vehicle will spawn with an owner ped. Owner ped will react based on location type (some will flee, some will fight). U need to get to the tow truck side of the vehicle.
{% endstep %}

{% step %}
**Attach the vehicle**

Drive your tow truck near the repo vehicle (within 4m). The vehicle will auto-attach to your tow truck. U will see "vehicle attached" status. Now u have a new gps marker to the dropoff location.
{% endstep %}

{% step %}
**Tow to dropoff**

Follow gps to the dropoff location (impound). Dropoff location is selected by server (500m+ away from pickup). U will see progress as u drive. Careful with turns and speed - towing slows u down.
{% endstep %}

{% step %}
**Complete the repo**

Arrive at dropoff location. Vehicle will auto-detach from tow truck. U will see "task completed" message. Payment is processed based on vehicle type (normal/highend/exotic). New task will be dispatched after cooldown.
{% endstep %}

{% step %}
**Test levels**

To test all vehicle types and perks, use `/setcivlevel repo 5` (testing command). This gives u level 5 status immediately. Now u can access exotic vehicles with full bonuses. Test level 1 vs level 5 to see difference in pay and available vehicles.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All repo locations, vehicle types, payment amounts, level requirements, challenges, and owner behaviors are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet integration
{% endcontent-ref %}

