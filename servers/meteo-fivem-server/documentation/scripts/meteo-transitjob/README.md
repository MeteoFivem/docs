---
description: >-
  Meteo transit - advanced bus transit job, drive routes, pick up passengers at stops, higher earnings than taxi.
---

# Meteo Transit Job

Advanced bus transit job. Drive routes, pick up passengers at multiple stops, drop them off. Multi-stop routes with higher earnings than taxi.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-transitjob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Transit Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to transit station location (or use `/tp 449.5959, -650.5834, 28.4790, 240.2101` for main dispatcher). Talk to the npc and pick up your bus. Get in the driver seat and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to transit job. Click "clock in" button. Make sure u are in the bus driver seat (required). Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept route task**

Server will dispatch a new bus route automatically. U will see route type, stops, and passenger count. Click "accept task" to start. GPS will route u to first passenger stop. Follow the gps marker.
{% endstep %}

{% step %}
**Board passengers at stop**

Drive to each marked stop location (within 15m). When u arrive at a stop, progress bar appears for boarding. Passengers board into bus. If u move vehicle during boarding, boarding is cancelled. Keep vehicle stationary until all passengers board. Once boarding complete, u see next gps marker.
{% endstep %}

{% step %}
**Drive between stops**

Follow gps to next stop on the route. Drive carefully - passengers are on board. If u drive too fast or crash, passengers might get angry. Stop at each marked location until all stops visited.
{% endstep %}

{% step %}
**Complete the route**

After all stops are visited and passengers dropped off, u will see "route completed" message. Payment is processed based on route type and passengers. Earnings show in task history. New route will be dispatched after cooldown.
{% endstep %}

{% step %}
**Test challenges**

Some routes have challenge timers (30% chance). Challenges require completing route within time limit. Bonus payment if completed on time. Challenge timer calculated from full route distance. Bonus based on time remaining. Challenge timer shown in tablet.
{% endstep %}

{% step %}
**Test night bonus**

Night bonus applies 22:00-06:00 in-game time. Requires level 2 or higher. Gives +15% bonus on top of route pay. Use `/time` command to test different times (only for admins).
{% endstep %}

{% step %}
**Test levels**

To see all available routes quickly, use `/setcivlevel transit 5` (testing command). This gives u level 5 status immediately. Now u have access to all route types and see all variants. Complete short, medium, and long routes to test different earnings.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All transit routes, stops, passenger counts, payment amounts, level bonuses, challenges, and vehicle deposits are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet integration
{% endcontent-ref %}

{% content-ref url="../meteo-timelimit/" %}
[meteo-timelimit](../meteo-timelimit/) - for challenge timers
{% endcontent-ref %}

