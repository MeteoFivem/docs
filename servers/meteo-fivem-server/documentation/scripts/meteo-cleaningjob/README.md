---
description: >-
  Meteo cleaning - group cleaning job with minigame spots, clean locations, earn money per spot completed.
---

# Meteo Cleaning Job

Group cleaning job. Clean multiple spots in a location, use minigame for each spot, earn money per spot completed. Works solo or with group.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-cleaningjob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Cleaning Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to cleaning job dispatcher location (or use `/tp -105.7079, -69.0300, 58.8590, 281.9016`). Talk to the npc and pick up a cleaning van. Get in the vehicle and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to cleaning job. Click "clock in" button. Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept a task**

Server will dispatch a new cleaning task automatically. U will see task location with number of cleaning spots. Click "accept task" to start. GPS will route u to the task location. Follow the gps marker.
{% endstep %}

{% step %}
**Find cleaning spots**

Arrive at task location (within area radius). U will see cleaning spots marked on map (trash piles, dirty areas, etc). Approach each spot and interact with ox_target/qb-target.
{% endstep %}

{% step %}
**Clean the spot**

Select "clean spot" option. Minigame starts - complete the cleaning action. Each spot gives immediate payment after completion.
{% endstep %}

{% step %}
**Complete the task**

After all spots are cleaned at the location, u will see "task completed" message. Payment processed for all cleaned spots + completion bonus. Earnings show in task history. New task dispatched after cooldown.
{% endstep %}

{% step %}
**Test with groups**

Open tablet and click "create group" to start a group. Or u can see existing groups and ask to join one. Group leader can invite friends. Members see the same task location and can help clean spots.
{% endstep %}

{% step %}
**Test group payment**

When in a group, all members see the same task location. Each member can clean different spots independently. All cleaned spots count toward task completion. When all spots are cleaned, entire group gets paid. All members get full payment (Config.memberCompletionPercent = 100%).
{% endstep %}

{% step %}
**Test levels**

To see all spot locations and perks instantly, use `/setcivlevel cleaning 5` (testing command). This gives u level 5 status immediately. Now u have access to all cleaning spot locations. Test level 1 vs level 5 to see difference in pay and available locations.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All spot locations, payment amounts, level requirements, challenges, and vehicle deposits are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for group system and tablet
{% endcontent-ref %}

