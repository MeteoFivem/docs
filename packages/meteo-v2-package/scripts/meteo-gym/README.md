---
description: >-
  Meteo gym - train strength, dexterity and endurance with an energy system,
  injuries and gyms built in-game, designed exclusively for the Meteo V2
  package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-gym/
---

# Meteo Gym

This is a guide about testing the Meteo V2 gym script designed exclusively for the Meteo V2 package. The gym is simplified - train on machines to raise strength, dexterity and endurance, watch your energy, and keep training or your stats slowly fade. It is connected with meteo-buffs (gym supplements), meteo-medicaljob (gym injuries), meteo-inventory (Status tab) and meteo-perks.

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

## Testing Gym

### Checking Your Stats

{% stepper %}
{% step %}
Open your inventory with **TAB** and use **Q** / **E** to go to the **Status** tab
{% endstep %}

{% step %}
Under **Physical Form** you can see your strength, dexterity and endurance, your overall shape, your gym energy and when it will be full again. If a stat is fading because you have not trained, it shows there too
{% endstep %}
{% endstepper %}

### Working Out

{% stepper %}
{% step %}
Go to any gym. The main gym is Muscle Sands Gym on the map (has a blip)

Or teleport: `/tp -1201.72, -1565.24, 4.61`

There are also gyms inside the prison for jailed players
{% endstep %}

{% step %}
Target any machine and start training. The target shows how much energy that set costs. There are 5 exercises:

* Pull-Up Bar, Bench Press and Barbell Curls (mainly strength)
* Push-Ups (mainly endurance)
* Dumbbell Workout (mainly dexterity)
{% endstep %}

{% step %}
Each rep has a minigame. The more reps you finish the more you gain, and a full set gives the most. Your stats go up to 100 and gains get slower the higher a stat is
{% endstep %}

{% step %}
Every set takes energy, hunger and thirst. Energy refills over time, but only while you are not too hungry or thirsty, so eat and drink to recover
{% endstep %}
{% endstepper %}

### What Stats Do

* **Strength** - more melee damage
* **Dexterity** - faster sprint speed
* **Endurance** - more stamina

### Gym Supplements

* Spawn `creatine` and use it before working out. Better gains, less energy per set and more stamina for 15 minutes
* Spawn `steroids` for a much bigger boost for 20 minutes. Careful, you can get hooked on them :)
* You will see the boost on the set done notification

{% content-ref url="../meteo-buffs/" %}
[meteo-buffs](../meteo-buffs/)
{% endcontent-ref %}

### Injuries

* If you do badly on a set you might hurt yourself (sore muscles, pulled muscle, sprained wrist or back strain)
* Injuries come from [meteo-medicaljob](../meteo-medicaljob/) and reduce your gains until they are treated or heal

***

## Testing the Creator

Admins can build gyms in-game. Open the admin menu with **F9** and go to **Script Settings** > **Creator** > **Gyms**.

{% stepper %}
{% step %}
Add a gym, give it a name, aim at the middle of the gym and set its map blip
{% endstep %}

{% step %}
Add machines. For each one pick the exercise, then either use a machine that is already in the map or spawn one of our gym props
{% endstep %}

{% step %}
Place the body spot - a ghost does the exercise so you can line it up on the machine. Save and go train on it
{% endstep %}
{% endstepper %}

***

## Test Commands

{% hint style="warning" %}
These commands are only available on our showcase server so you can quickly check things. Also check out [test-commands](test-commands.md) for full details.
{% endhint %}

* `/gym info` - show your stats and energy
* `/gym set strength 50` - set a stat (strength, dexterity, endurance) from 0 to 100
* `/gym energy 100` - set your energy
* `/gym max` - max all stats and energy
* `/gym reset` - put all stats back to 0

***

## Good to Know

{% hint style="success" %}
Gyms and their machines are editable in-game with the **Gyms** creator, and the energy cost and stat gains of every exercise plus the perk XP per set are editable from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* Stats start to fade if you do not train for a day, so keep working out
* Finishing a full set gives XP on the **Fitness** line in [meteo-perks](../meteo-perks/)
