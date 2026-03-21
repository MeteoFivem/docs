---
description: >-
  Meteo weapon repair - repair weapons with materials script
  designed exclusively for the meteo fivem server.
---

# Meteo Weapon Repair

This is a guide about testing the meteo fivem weapon repair script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-weaponrepair-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Weapon Repair

{% stepper %}
### Get a weapon and damage it

Get weapon using `/giveitem yourid weapon_pistol_mk2 1` or use meteo admin menu. Use the weapon till its health is lower. You can see the weapon health on inventory when hovering on weapon item.

### Go to repair location

Use `/tp 2409.2043, 3031.5886, 48.1526` on chat to teleport there.

### Store the weapon

Point target at the repair bench and open storage. Put the weapon to that slot (you can repair 2 weapons at a time - this is configurable).

### Check repair cost

Point target and use repair weapon option. This will show what materials and cost you need to repair the weapon. Repair cost is $500 per weapon. Materials needed: plastic, metalscrap, copper, aluminum, steel, rubber (2 to 4 items needed depending on damage).

### Get the materials

Usually they are materials which players can find on scrap and dumpsters like doing those activities. You can open admin menu using **F9** and spawn those items. Or use commands like `/giveitem yourid metalscrap 5`, `/giveitem yourid plastic 5` etc.

### Repair the weapon

After that confirm repair and do the minigame and finish it. The skill check has 3 rounds with mixed difficulty (easy, medium, hard). If you fail you keep your materials - just try again. Finally open storage again and get the repaired weapon.
{% endstepper %}

{% hint style="warning" %}
The `/giveitem` and `/tp` commands are only available on our test server so you can quickly get materials and teleport.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
All repair costs, materials, skill check difficulty and locations are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Repair bench location has an optional map blip that can be enabled in config
