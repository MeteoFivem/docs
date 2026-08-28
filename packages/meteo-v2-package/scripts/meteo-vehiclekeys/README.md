---
description: >-
  Meteo vehicle keys - locks, keys, lockpicking and hotwiring designed
  exclusively for the meteo fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-vehiclekeys/
---

# Meteo Vehicle Keys

This is a guide about testing the meteo fivem vehicle keys script designed exclusively for meteo server.

Every vehicle on the map has a lock state and an owner. Your own cars you just unlock. Anything else you have to get into the hard way, and how hard depends on what you are trying to steal.

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
* Get a lockpick with `/giveitem yourid lockpick 1` and an advanced one with `/giveitem yourid advancedlockpick 1`

***

## Testing Vehicle Keys

### Keybinds

| Key | What it does |
| --- | ------------ |
| **L** | Lock or unlock the closest vehicle you have keys to |
| **G** | Toggle the engine while you are in the driver seat |
| **H** | Search the cabin for keys when you are in a car you do not have keys to |

### Your Own Vehicles

{% stepper %}
{% step %}
Take a car out of your [garage](../meteo-garages/) and walk away from it
{% endstep %}

{% step %}
Press **L** within 5 meters to lock and unlock it
{% endstep %}

{% step %}
Owned vehicles are read from the database, so your keys survive a reconnect or a server restart
{% endstep %}
{% endstepper %}

### Stealing a Parked Car

{% stepper %}
{% step %}
Find a parked NPC vehicle. Most of them spawn locked
{% endstep %}

{% step %}
Target the door with a lockpick to pick it. Fail and there is a chance the lockpick snaps - a normal lockpick breaks far more often than an advanced one
{% endstep %}

{% step %}
Once you are in the driver seat you still need to hotwire it before the engine turns over
{% endstep %}

{% step %}
Failing a lockpick or a carjack has a good chance of alerting police, though the odds drop at night
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Cycles are never locked. Military vehicles and trains cannot be picked or hotwired at all.
{% endhint %}

### Difficulty by Vehicle Class

This is the part worth testing properly. The minigame gets harder the more expensive the car is.

| Class | What is in it | How it feels |
| ----- | ------------- | ------------ |
| S | Supers and open wheel | Brutal - long sequence, tight timing |
| A | Sports | Very hard |
| B | Muscle and sports classics | Hard |
| C | Coupes, sedans, motorcycles | Medium |
| D | Compacts, SUVs, offroad | Easy |
| E | Vans, industrial, utility, commercial | Easy |

Try picking a compact and then a super and you will feel the difference straight away. An advanced lockpick gives you 40% more time between circles on top of that.

Emergency vehicles get their own difficulty so a police cruiser is never an easy pick.

### Searching for Keys

{% stepper %}
{% step %}
Get into the driver seat of a car you do not have keys to
{% endstep %}

{% step %}
A prompt shows - press **H** to search the cabin
{% endstep %}

{% step %}
It takes 20 to 40 seconds and you might come up with nothing
{% endstep %}

{% step %}
Your odds depend on the car. A van or a beater often has keys in it, a sedan sometimes, and a super or a sports car never does
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Getting into the driver seat of a vehicle that is already running hands you the keys. That is the reward for catching someone who left their engine on.
{% endhint %}

### Sharing Keys

* `/givekeys` hands your keys to the closest person. Without an ID it gives them to everyone in the vehicle
* Job vehicles use shared keys instead - any on-duty police officer can use any police car, EMS can use the ambulance, mechanics can use the tow truck
* Every vehicle from [meteo-jobgarage](../meteo-jobgarage/) is registered for shared keys automatically

***

## Good to Know

{% hint style="success" %}
Lock chances, break chances, class difficulty, key search odds, police alert chance, shared job keys and carjacking are all configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Reconnect within 30 minutes and the keys you picked up that session come back
* Carjacking NPC drivers at gunpoint is in the script but turned off by default, since GTA's own carjack behaviour is not reliable
* Wreck a car's doors badly enough and the cabin is open regardless of the lock

{% content-ref url="../meteo-garages/" %}
[meteo-garages](../meteo-garages/)
{% endcontent-ref %}

{% content-ref url="../meteo-jobgarage/" %}
[meteo-jobgarage](../meteo-jobgarage/)
{% endcontent-ref %}

{% content-ref url="../meteo-boosting/" %}
[meteo-boosting](../meteo-boosting/)
{% endcontent-ref %}

{% content-ref url="../meteo-minigames/" %}
[meteo-minigames](../meteo-minigames/)
{% endcontent-ref %}
