---
description: >-
  Meteo buffs - item effects, cravings and withdrawal built in-game from the
  admin menu, designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-buffs/
---

# Meteo Buffs

This is a guide about testing the Meteo V2 buffs script designed exclusively for the Meteo V2 package. This script decides what happens when a player uses an item - faster movement, more stamina, less damage taken, wobbly vision, better gym gains and more - and what they start craving if they keep using it. The whole system is simplified and everything is built in-game, so adding a new drug, energy drink or detox pill needs no code. Connected with meteo-hud, meteo-inventory, meteo-gym, meteo-perks and more.

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

## Testing Item Effects

{% stepper %}
{% step %}
Spawn a few items and use them:

* `/giveitem yourid meteo_donut 1`
* `/giveitem yourid beer 1`
* `/giveitem yourid joint 1`
{% endstep %}

{% step %}
Each one plays its own animation and progress bar. When it finishes you get a notification about what kicked in, and the effects show as buff and debuff icons on the HUD counting down
{% endstep %}

{% step %}
Open your inventory with **TAB** and use **Q** / **E** to go to the **Status** tab. You can see every running effect with the time left, plus your cravings and injuries. You can also use `/charstatus` for a quick list
{% endstep %}

{% step %}
Now use a `beer` again but cancel the progress bar halfway. You should get nothing - no effects, no thirst and the beer stays in your pocket
{% endstep %}
{% endstepper %}

### Meals and Gym Supplements

* Main dishes are worth eating. `/giveitem yourid meteo_taco 1` or `meteo_roast_chicken` gives a stamina boost for a few minutes. Sprint before and after to feel it
* `/giveitem yourid creatine 1` - better gym gains, less energy used per set and more stamina for 15 minutes
* `/giveitem yourid steroids 1` - a much bigger gym boost, more stamina and damage for 20 minutes. But you can get hooked on these :)

{% content-ref url="../meteo-gym/" %}
[meteo-gym](../meteo-gym/)
{% endcontent-ref %}

***

## Testing Cravings

Using the same kind of thing again and again gets you hooked. There are cravings for fast food, junk food, alcohol, weed, cocaine, meth, ecstasy, oxy and steroids.

{% stepper %}
{% step %}
Use the same kind of item a few times (for example `cokebaggy` or `meth`). Uses within the same minute count as one, so space them out
{% endstep %}

{% step %}
Once you are hooked, stay clean for a while and the craving starts. A badge shows on the HUD, the craving shows in the inventory Status tab and withdrawal effects (camera shake, slower movement and so on) keep firing
{% endstep %}

{% step %}
Use the item again and the craving stops. If you stay clean long enough you forget the habit completely
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Want to skip the grinding? Use `/buffs crave alcohol` to get hooked instantly. This command is only available on our showcase server. Also check out [test-commands](test-commands.md) for more details.
{% endhint %}

### Detox Items

These items cure cravings:

* `/giveitem yourid detox_pills 1` - works on alcohol and all drug cravings
* `/giveitem yourid rehab_drink 1` - strong cure for alcohol
* `/giveitem yourid detox_tea 1` - works on drug cravings (weed, cocaine, meth, ecstasy, oxy - not alcohol)

***

## Testing the Creator

Admins can build their own items and cravings in-game. Open the admin menu with **F9** and go to **Script Settings** > **Creator** > **Buffs**.

{% stepper %}
{% step %}
**Build a craving**

Add a record, set the type to **Craving**, give it a name and icon, set how many uses it takes to get hooked, how long staying clean takes to forget it, and the withdrawal effects
{% endstep %}

{% step %}
**Build an item**

Add another record, set the type to **Item** and pick any inventory item. Add effects (movement speed, stamina, damage, defense, healing, screen effect, walk style and more), each with a strength and a duration. Pick the craving it feeds, or the cravings it cures
{% endstep %}

{% step %}
**How it is used**

Pick a use type (eat, drink, smoke, pill and more) and the script handles the animation, prop, progress bar, hunger, thirst and stress for you. Or leave it to another script that already handles that item
{% endstep %}

{% step %}
Save, use the item in game and see your effects on the HUD and in the inventory Status tab
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
Every item effect, craving and withdrawal is editable in-game - add or edit them with the **Buffs** creator in **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates.
{% endhint %}

* The package comes with a ready made set of items and cravings (food, drinks, drugs, detox items, gym supplements and a stamina boost on restaurant main dishes) which you can edit or remove
* Effects and cravings last for the session. Logging out clears them
* The **Substances** perk line from [meteo-perks](../meteo-perks/) makes item effects last longer and cravings build up slower
