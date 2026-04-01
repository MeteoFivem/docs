---
description: >-
  Meteo taxi - simple and reliable taxi driver job, pick up passengers, drive to destination, earn money.
---

# Meteo Taxi Job

Simple and reliable taxi driver job. Pick up passengers, drive them to destination, get paid. Scale up with levels and achievements.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-taxijob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Taxi Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to any taxi stand location (or use `/tp 442.5959, -660.5834, 28.4790, 240.2101` for main taxi dispatcher). Talk to the npc and pick up your taxi vehicle. Get in the driver seat and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to taxi job. Click "clock in" button. Make sure u are in the taxi vehicle driver seat (this is required). Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept a task**

Server will dispatch a new task automatically. U will see pickup location and destination on map. Click "accept task" button to start. GPS will route u to pickup location. Follow the gps marker.
{% endstep %}

{% step %}
**Pick up passenger**

Drive to the pickup location (30m radius). When u get close (30m) an npc passenger will spawn. Drive closer until ped is within 5m and they will enter your taxi. U will see "passenger in vehicle" status and new gps marker to dropoff.
{% endstep %}

{% step %}
**Drop off passenger**

Follow gps to dropoff location. Once u arrive passenger will exit vehicle automatically. U will see "task completed" message. Payment is processed and shown in task history. New task will be dispatched after cooldown.
{% endstep %}

{% step %}
**Test challenges**

Sometimes u will get a "challenge" task (30% chance). Challenges have a timer - complete the route within the time limit. If u complete challenge on time, u get bonus payment. Bonus is calculated based on time left and distance. Challenge timer shows in tablet.
{% endstep %}

{% step %}
**Test night bonus**

Night bonus is unlocked at level 2. Once u reach level 2, night bonus applies 22:00-06:00 in-game time. Gives +15% bonus on top of base pay during night hours. Use `/time` command to test different times (only for admins). Example: `/time 12` for day, `/time 1` for night. To test: get level 2, set time to night, complete ride to see bonus applied.
{% endstep %}

{% step %}
**Test levels**

To test all perks quickly, use `/setcivlevel taxi 5` (testing command). This gives u level 5 status immediately. Now all perks are active - u can see bonus in earnings. Complete rides with level 5 vs level 1 to compare payouts.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All taxi locations, pickup zones, payment amounts, level bonuses, challenges, and vehicle deposits are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet integration
{% endcontent-ref %}

{% content-ref url="../meteo-timelimit/" %}
[meteo-timelimit](../meteo-timelimit/) - for challenge timers
{% endcontent-ref %}

