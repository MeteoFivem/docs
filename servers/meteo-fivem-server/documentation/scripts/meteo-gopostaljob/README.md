---
description: >-
  Meteo go postal - group postal delivery job, deliver packages to multiple addresses, earn money per delivery.
---

# Meteo Go Postal Job

Group postal delivery job. Deliver packages to multiple addresses on a route, earn money per delivery. Works solo or with group. Highest paying job.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-gopostaljob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Go Postal Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet.
{% endstep %}

{% step %}
**Go to dispatcher**

Go to postal office dispatcher location. Talk to the npc and pick up a postal van (boxville or work vehicle). Get in the vehicle and open tablet.
{% endstep %}

{% step %}
**Clock in**

Open tablet and go to go postal job. Click "clock in" button. Once clocked in u will see "waiting for task" status.
{% endstep %}

{% step %}
**Accept delivery task**

Server will dispatch a new postal route automatically. U will see delivery route with multiple packages and addresses. Click "accept task" to start. GPS will route u to first delivery address. Follow the gps marker.
{% endstep %}

{% step %}
**Deliver packages**

Drive to each marked delivery address. U will see gps marker for each delivery point. Stop near building/house entrance. Approach package location and interact to deliver. Each delivery = immediate payment.
{% endstep %}

{% step %}
**Complete the route**

After all packages are delivered at all addresses, u will see "route completed" message. Payment processed for all deliveries + completion bonus. Earnings show in task history. New route dispatched after cooldown.
{% endstep %}

{% step %}
**Test with groups**

Open tablet and click "create group" to start a group. Or u can see existing groups and ask to join one. Group leader can invite friends. Members see the same delivery route and can help deliver packages.
{% endstep %}

{% step %}
**Test group work**

When in a group, all members see the same delivery route. Packages shared across group members. Leader can distribute packages or all grab their own. Group can split up and deliver different packages simultaneously. When all packages delivered, entire group gets paid. All members get full payment (Config.memberCompletionPercent = 100%).
{% endstep %}

{% step %}
**Test levels**

To see all postal routes and perks instantly, use `/setcivlevel gopostal 5` (testing command). This gives u level 5 status immediately. Now u have access to all postal delivery routes. Test level 1 vs level 5 to see difference in pay and packages per route.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All delivery locations, package counts, payment amounts, level requirements, challenges, and vehicle deposits are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for group system and tablet
{% endcontent-ref %}

