---
description: >-
  Meteo vault job - bank vault robbery script designed exclusively for the meteo
  fivem server.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-vaultjob/
---

# Meteo Vault Job

This is a guide about testing the Meteo V2 bank vault robbery script designed exclusively for the Meteo V2 package.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

{% hint style="warning" %}
Make sure to follow the [meteo-crimetablet](../meteo-crimetablet/) guide before following this.
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Vault Job

### Purchasing

{% stepper %}
{% step %}
#### Purchase the Service

Open tablet and go to services app. You can see the Vault Job service. Purchase it (costs 350 MTC) and start
{% endstep %}

{% step %}
#### Add Group Members (Optional)

You can do this with a group too. Follow group guide on [crimetablet](../meteo-crimetablet/) guide and add group members too
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
If you do not have crypto use `/addcrypto 400` and get crypto. This is a testing command and only works on our showcase server
{% endhint %}

### Doing the Vault Job

{% stepper %}
{% step %}
#### Go to the Bank

After purchasing check the map. You will see the marked bank location. Go there with armor. Also group members can see these too like our other services
{% endstep %}

{% step %}
#### Clear the Guards

Kill the guards and make sure to loot them too
{% endstep %}

{% step %}
#### Hack the Door

You need `electronickit` and `trojan_usb` to hack the security panel (both get used up). Complete the hacking minigame to open the vault door. If you fail the hack you lose 60 seconds from the timer. Police get an alert on [meteo-mdt](../meteo-mdt/) when the vault opens
{% endstep %}

{% step %}
#### Loot the Vault

Then you need a `drill` to drill the deposit boxes inside the vault. Watch the heat in the drilling minigame, the drill can break if it overheats. Also grab the money trolleys to get their items
{% endstep %}

{% step %}
#### Escape

Make sure to escape before the timer (15 minutes) runs out. Otherwise bank door will automatically close and reset the hunt. Completion rewards: 600 MTC and 75 rep
{% endstep %}
{% endstepper %}

> Also like other hunts this one also has auto reset if you die etc

***

## Good to Know

{% hint style="success" %}
Rewards, the security panel hack, deposit box loot, money cart loot, guard loot, fingerprint chance, stress and perk XP are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit banks (security panel, deposit boxes, trolleys and guards) in-game with the Banks creator.
{% endhint %}

> Connected with [meteo-perks](../meteo-perks/). With the Vault Jobs perk line - Ghost Protocol reduces dispatch calls, Backdoor lets you crack extra deposit boxes, Exploit reduces the vault hack fail penalty, Phantom reduces vault cooldowns, Ransomware gives a chance to find bonus crypto, Zero Day drops hack minigame difficulty, Zero Trace makes cops take longer to respond and Master Hacker increases hack payouts

{% content-ref url="../meteo-crimetablet/" %}
[meteo-crimetablet](../meteo-crimetablet/)
{% endcontent-ref %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
