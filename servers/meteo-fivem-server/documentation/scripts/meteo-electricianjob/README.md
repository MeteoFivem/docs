---
description: >-
  Meteo electrician - group electrician job with fuse box repairs, earn money per box repaired.
---

# Meteo Electrician Job

Group electrician job. Repair electrical fuse boxes with minigame, earn money per box repaired. Works solo or with group. Harder than cleaning, better pay.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-electricianjob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Electrician Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to electrician dispatcher location. Talk to the npc and pick up a work van. Get in the vehicle and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to electrician job. Click "clock in" button. Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept electrical task**

Server will dispatch a new electrical task automatically. U will see task location with number of fuse boxes to repair. Click "accept task" to start. GPS will route u to the task location. Follow the gps marker.
{% endstep %}

{% step %}
**Find electrical boxes**

Arrive at task location (within area radius). U will see electrical fuse boxes marked on map. Boxes are networked entities spawned when task starts. Boxes have fire particle effects (unrepaired boxes are burning). Approach each box and interact with ox_target/qb-target.
{% endstep %}

{% step %}
**Repair with minigame**

Select "repair box" option on the box. Fuse box minigame starts (meteo-fuseboxfix) - complete it to repair. Success: box repaired, fire effect removed, u get paid. Failure: u get electrocuted (shock animation + damage), need to retry. Each successful repair = immediate payment.
{% endstep %}

{% step %}
**Complete the task**

After all boxes are repaired at the location, u will see "task completed" message. Payment processed for all repaired boxes + completion bonus. Earnings show in task history. New task dispatched after cooldown.
{% endstep %}

{% step %}
**Test with groups**

Open tablet and click "create group" to start a group. Or u can see existing groups and ask to join one. Group leader can invite friends. Members see the same task location and can help repair boxes.
{% endstep %}

{% step %}
**Test group work**

When in a group, all members see the same task location. Each member can repair different boxes independently. All repaired boxes count toward task completion. When all boxes are repaired, entire group gets paid. All members get full payment (Config.memberCompletionPercent = 100%).
{% endstep %}

{% step %}
**Test levels**

To see all electrical locations and perks instantly, use `/setcivlevel electrician 5` (testing command). This gives u level 5 status immediately. Now u have access to all electrical task locations. Test level 1 vs level 5 to see difference in pay and boxes per task.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All electrical locations, box counts, payment amounts, minigame difficulty, challenge settings, and vehicle deposits are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for group system and tablet
{% endcontent-ref %}

{% content-ref url="../meteo-fuseboxfix/" %}
[meteo-fuseboxfix](../meteo-fuseboxfix/) - for the fuse box repair minigame
{% endcontent-ref %}

