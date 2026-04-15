---
description: >-
  Meteo repo job - vehicle repossession job with 3 vehicle tiers, owner ped AI
  behaviors, level-based unlocks and challenge timers designed exclusively for
  the meteo fivem server.
---

# Meteo Repo Job

This is a guide about testing the meteo fivem repo job script designed exclusively for meteo server. vehicle repossession job with 3 vehicle tiers (normal, highend, exotic), owner ped AI behaviors per location type (flee, fight, weapon), level-based vehicle unlocks, challenge timers and deposit-based vehicle damage penalties.

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
* Have the [job tablet](../meteo-jobtablet/) ready

***

## Testing Repo Job

{% stepper %}
{% step %}
**Get the tablet and go to dispatcher**

use `/giveitem id meteo_jobtablet` to spawn the tablet. go to repo office location (or use `/tp 498.4681, -1340.0299, 29.3143, 8.2895` for main dispatcher). talk to the npc and pick up your tow truck. get in the driver seat and open tablet
{% endstep %}

{% step %}
**Clock in**

open tablet and go to repo job. click "clock in" button. make sure you are in tow truck driver seat (required). once clocked in you will see "waiting for task" status
{% endstep %}

{% step %}
**Accept a repo task**

server will dispatch a new repo target automatically. you will see the vehicle location, type (normal/highend/exotic), and pickup spot. click "accept task" to start. gps will route you to the vehicle location. follow the gps marker
{% endstep %}

{% step %}
**Locate the vehicle**

drive to the marked repo location. when you get within 30m the repo vehicle will spawn with an owner ped. owner ped will react based on location type (some will flee, some will fight). you need to get to the tow truck side of the vehicle
{% endstep %}

{% step %}
**Attach the vehicle**

drive your tow truck near the repo vehicle (within 4m). the vehicle will auto-attach to your tow truck. you will see "vehicle attached" status. now you have a new gps marker to the dropoff location
{% endstep %}

{% step %}
**Tow to dropoff**

follow gps to the dropoff location (impound). dropoff location is selected by server (500m+ away from pickup). you will see progress as you drive. careful with turns and speed - towing slows you down
{% endstep %}

{% step %}
**Complete the repo**

arrive at dropoff location. vehicle will auto-detach from tow truck. you will see "task completed" message. payment is processed based on vehicle type (normal/highend/exotic). new task will be dispatched after cooldown
{% endstep %}
{% endstepper %}

***

## Understanding Vehicle Types

* normal vehicles: standard cars (lower pay)
* highend vehicles: sports cars, luxury vehicles (medium pay)
* exotic vehicles: rare supercars (highest pay)
* vehicle type determines base payment
* higher level repos unlock access to more valuable vehicles

***

## Understanding Earnings

* base pay depends on vehicle type (not distance like taxi)
* normal: \~$500-700 base
* highend: \~$1000-1500 base
* exotic: \~$2000-3000 base
* challenge bonus applies if you complete within time limit
* payment shown with breakdown in tablet

***

## Levels And Perks

* level 1: base earn on normal vehicles only
* level 2: unlock highend vehicles (+15% pay)
* level 3: unlock exotic vehicles (+25% pay + better perks)
* level 4: +30% pay bonus on all types
* level 5: +40% pay + all perks + highest value repos
* complete more repos and earn xp to level up
* check tablet rankings to see where you stand

***

## Achievements

* complete 5 repos
* complete 25 repos
* complete 100 repos
* repo 5 exotic vehicles
* repo 10 exotic vehicles
* earn $25,000 from repos
* earn $150,000 from repos
* each achievement tracks progress

***

## Location Types

repo locations have different types with different owner ped behaviors:

* residential: owner might flee or call police
* street: owner might be aggressive, fight back
* highway: owner might have weapon
* industrial: multiple owners or dangerous situation
* higher danger = better pay but harder task

***

## Testing Challenges

repo tasks have challenge timers based on route distance. tow trucks are slower so more time is given than taxi. complete within time to get bonus payment. bonus calculated by time left and distance. challenge timer visible in tablet

***

## Testing Vehicle Damage

if you damage tow truck, deposit refund is reduced. damaged vehicle = worse job performance = less earnings. try completing repos with clean vs damaged tow truck

***

## Testing With Levels

to test all vehicle types and perks, use `/setcivlevel repo 5` (testing command). this gives you level 5 status immediately. now you can access exotic vehicles with full bonuses. test level 1 vs level 5 to see difference in pay and available vehicles

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
repo vehicles spawn as local entities at location (not persistent). owner ped behavior (fight/flee/weapon) is configured per location type in Config.pedBehavior. vehicle type pool determined by Config.locationVehicleType mapping locations to normal/highend/exotic. challenge time auto-calculated from total tow distance (server side). dropoff location selected by server (at least 500m from pickup). tow truck attach distance is 4m (auto-attach when close enough). vehicle health tracked - Config.vehicleDamage affects deposit refund. once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/)
{% endcontent-ref %}
