---
description: >-
  Meteo scenes - 3D scenes, graffiti and territory marking script designed
  exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-scenes/
---

# Meteo Scenes

This is a guide about testing the Meteo V2 3D scenes and graffiti script designed exclusively for the Meteo V2 package.

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

## Testing Scenes

### Creating a Scene

{% stepper %}
{% step %}
#### Open the creator

Spawn `marking_spray` using `/giveitem yourid marking_spray 1` and use it from your inventory. As an admin you can also use `/scene` command on chat to open the creator without the item.
{% endstep %}

{% step %}
#### Design it

Pick a preset (Street Tag, King Piece, Throw Up, Neon Sign, Old Paper and more) or start from scratch. You can add up to 8 text and decal elements and customize the font (25 graffiti, handwritten, horror, display and clean fonts), colour, spray or clean paint style, effects, size and rotation. You can also pick a background.
{% endstep %}

{% step %}
#### Place it

Aim at a wall and place it. By default the scene sticks flat to the surface you aim at, or you can set it to face the player. You can also choose when it is visible and how long it stays (player scenes expire, up to 7 days).
{% endstep %}
{% endstepper %}

### Removing a Scene

* Spawn `paint_remover` and use it while aiming at a scene to remove it
* As an admin you can use `/deletescene` on chat to remove the scene you aim at
* Anyone can use `/hidescenes` to hide or show scenes for themselves

### Organization Territory

* This is connected to our crime system organizations. Graffiti placed by an organization member counts as territory for that organization and shows on the crimetablet
* Rival organizations can remove it with `paint_remover` by passing a skill check and get organization XP for it

### Admin Panel

* As an admin use `/sceneadmin` on chat to open the admin panel
* You can see all scenes with filters, teleport to them, delete them and manage the custom image library (allowed image links players can use as backgrounds)

{% hint style="warning" %}
The `/giveitem` command is only available on our showcase server so you can quickly spawn items.
{% endhint %}

### Check out the testing video for more details :)

***

## Good to Know

{% hint style="success" %}
All scene settings like render distance, fonts, presets, backgrounds, expiry times, territory rewards and allowed image hosts are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-organizations/" %}
[meteo-organizations](../meteo-organizations/)
{% endcontent-ref %}
