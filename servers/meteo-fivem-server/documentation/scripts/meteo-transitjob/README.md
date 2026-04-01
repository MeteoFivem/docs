---
description: >-
  Meteo transit job - advanced bus transit job designed exclusively for the meteo
  fivem server.
---

# Meteo Transit Job

This is a guide about testing the meteo fivem transit job script designed exclusively for meteo server. advanced bus transit job. drive routes, pick up passengers at multiple stops, drop them off. multi-stop routes with higher earnings than taxi.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-transitjob-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Have the [job tablet](../meteo-jobtablet/) ready

***

## Testing Transit Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to transit station location (or use `/tp 449.5959, -650.5834, 28.4790, 240.2101` for main dispatcher). talk to the npc and pick up your bus. get in the driver seat and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to transit job. click "clock in" button. make sure u are in the bus driver seat (required). once clocked in u will see "waiting for task" status
{% endstep %}

{% step %}
**Accept a route task**

server will dispatch a new bus route automatically. u will see route type, stops, and passenger count. click "accept task" to start. gps will route u to first passenger stop. follow the gps marker
{% endstep %}

{% step %}
**Board passengers at stops**

drive to each marked stop location (within 15m). when u arrive at a stop, progress bar appears for boarding. passengers board into bus (Config.boardingDuration per stop). if u move vehicle during boarding, boarding is cancelled. keep vehicle stationary until all passengers board. once boarding complete, u see next gps marker
{% endstep %}

{% step %}
**Drive between stops**

follow gps to next stop on the route. drive carefully - passengers are on board. if u drive too fast or crash, passengers might get angry. stop at each marked location until all stops visited
{% endstep %}

{% step %}
**Complete the route**

after all stops are visited and passengers dropped off, u will see "route completed" message. payment is processed based on route type and passengers. earnings show in task history. new route will be dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Route Types

* short routes: 4-5 stops, quick completion, lower pay
* medium routes: 5-6 stops, moderate distance, medium pay
* long routes: 7-8 stops, long distance, higher pay
* each route type has multiple task variants with different stop sequences
* route type determines base payment

***

## Understanding Earnings

* base pay depends on route type (not distance like taxi)
* bonus per passenger (Config.passengerBonus)
* rush hour affects passenger count (more passengers during rush times)
* earnings = route base + (passengers x passenger bonus)
* payment shown with breakdown in tablet

***

## Rush Hour Mechanics

passenger count varies based on time of day. peak hours (morning, evening): more passengers per stop. off-peak hours: fewer passengers. rush hour multiplier configured in Config.rushHour. more passengers = higher earnings but longer boarding times

***

## Levels And Perks

* level 1: base earn on short routes only
* level 2: unlock medium routes (+10% pay)
* level 3: unlock long routes (+20% pay + xp bonus)
* level 4: +30% pay bonus + night bonus (22:00-06:00 +15% pay)
* level 5: +40% pay + all perks + highest pay routes
* complete routes and earn xp to level up
* check tablet rankings to see where u stand

***

## Achievements

* complete 10 routes
* complete 50 routes
* transport 500 passengers total
* transport 2000 passengers total
* earn $50,000
* earn $250,000
* complete perfect route (no damage, no cancellations)
* each achievement tracks progress

***

## Testing Challenges

some routes have challenge timers (30% chance). challenges require completing route within time limit. bonus payment if completed on time. challenge timer calculated from full route distance. bonus based on time remaining. challenge timer shown in tablet

***

## Testing Night Bonus

night bonus applies 22:00-06:00 in-game time. requires level 2 or higher. gives +15% bonus on top of route pay. use `/time` command to test different times (only for admins)

***

## Testing Boarding Mechanics

boarding is time-based progress bar (Config.boardingDuration per stop). if u move vehicle during boarding, progress cancels and resets. keep vehicle still for full boarding duration. multiple passengers board simultaneously at each stop. passenger count per stop affects boarding time

***

## Testing All Routes

to see all available routes quickly, use `/setcivlevel transit 5` (testing command). this gives u level 5 status immediately. now u have access to all route types and see all variants. complete short, medium, and long routes to test different earnings

***

## Testing Vehicle Damage

if u damage the bus too much, u lose part of your deposit. deposit refund based on vehicle damage percent. damaged bus = reduced earnings. try completing routes with clean vs damaged bus

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
routes configured in Config.busRoutes with multiple task variants per route type. each route has specific stop sequence and passenger counts. passenger models vary by route type (Config.passengerModels). stop arrival distance is 15m (Config.stopArrivalDistance). boarding duration configurable per stop (Config.boardingDuration). rush hour multipliers affect passenger count, not distance. challenge timer auto-calculated from total route distance. vehicle damage tracked - Config.vehicleDamage has penalty thresholds. passenger peds are local entities (spawn and despawn per stop). once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet, groups, achievements, rankings
{% endcontent-ref %}
