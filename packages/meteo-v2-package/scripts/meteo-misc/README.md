---
description: >-
  Meteo misc - vehicle push, crouch, consumables, diving gear and more designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-misc/
---

# Meteo Misc

This is a guide about testing the Meteo V2 package misc features.

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

## Testing Features

### Push Vehicle

* After vehicle engine dead or body has lot of damage or fuel low then you can point target to vehicle and push the vehicle
* Use A and D to turn left and right while pushing and E to stop push

### Seat Shuffle

* Use **O** key to shuffle to other side of the seat. So no need to use f1 menu and change seats everytime

### Vehicle Trunk (Boot)

{% stepper %}
{% step %}
Open a vehicle's boot (make sure the car is unlocked), then target the boot and choose to climb in
{% endstep %}

{% step %}
While inside press **E** to climb out and **G** to pop the boot open or shut from the inside

A locked car keeps you shut in - someone has to unlock it and pull you out, or the lid has to be gone
{% endstep %}

{% step %}
Another player can target the open boot and pull you out. Police can also stuff a cuffed or downed suspect into a boot
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Every vehicle works out of the box - the pose inside the boot is worked out from the shape of the boot. Admins can fine-tune it per model with `/trunkadjust` next to the vehicle, or Admin menu > Script Settings > Misc > Boot Poses. Arrows move, numpad +/- changes height, Q/E turns, A/D tilts, hold Shift to move faster, R starts over, G previews the lid and ENTER saves. The pose is synced for everyone with no restart.
{% endhint %}

### Vehicle Shooting (First Person Aim)

{% stepper %}
{% step %}
Get `/giveitem yourid weapon_pistol 1` and use `/car adder`
{% endstep %}

{% step %}
Shooting inside vehicle it will update the shoot camera to first person aim (similar to prp)

Works with bikes, helicopters, boats and normal vehicles
{% endstep %}
{% endstepper %}

### Zoom Camera

* Hold the mouse wheel button to zoom the camera
* Zoom is blocked while holding a weapon by default

### Crouch

* Use **K** key to toggle crouch
* Crouch animation syncs with other players too

### Meditation

{% stepper %}
{% step %}
Go to `/tp 2460.56, 3777.03, 42.03` and use E to meditate
{% endstep %}

{% step %}
Meditation relieves stress for your character. You need at least 20 stress to start

There are 7 meditation spots around the map and the nearest one shows on your map
{% endstep %}

{% step %}
Admins can add, move or remove meditation spots in game: Admin menu > Script Settings > Misc > Creator
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Food, drinks, alcohol and drug consumables are now handled by [meteo-buffs](../meteo-buffs/).
{% endhint %}

### Diving Gear

{% stepper %}
{% step %}
Spawn `diving_gear` item and use it to equip diving suit with oxygen tank
{% endstep %}

{% step %}
Go underwater and your oxygen drains slowly. You can hear breathing sounds while diving
{% endstep %}

{% step %}
Spawn `diving_fill` item to refill your oxygen tank

Oxygen level is saved on the item so it remembers how much you have left
{% endstep %}
{% endstepper %}

### Elevator

{% stepper %}
{% step %}
There is an elevator at city hall. Go near and press **E** to use it and travel between floors
{% endstep %}

{% step %}
Admins can build elevators in game: Admin menu > Script Settings > Misc > Creator. Name the building, add its floors, then stand in each doorway to place the doors

Add the doors in the same order on every floor, so door 1 upstairs is the same lift as door 1 downstairs. Saving applies for everyone with no restart
{% endstep %}
{% endstepper %}

### Inspect Overlay

* Hold **HOME** to show the citizen ID above nearby players (including you) and the class of nearby occupied vehicles
* Release the key to hide it again

### AFK Kick

* If a player is afk for 15 minutes they get kicked automatically
* Players get warning notifications before they are kicked
* Admin and god groups are immune to this

***

## Good to Know

{% hint style="success" %}
Add or edit elevators, meditation spots and boot poses in-game with the Misc Records creator, and tune boot poses from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

{% hint style="info" %}
Other values like vehicle push damage threshold, zoom settings, afk kick time, diving oxygen and the inspect key are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}
