---
description: >-
  Meteo whiteboard - placeable synced whiteboards that render videos and
  images, designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-whiteboard/
---

# Meteo Whiteboard

This is a guide about testing the Meteo V2 whiteboard script designed exclusively for the Meteo V2 package. Place a board anywhere and play videos or images on it, synced for everyone nearby.

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

## Testing Whiteboard

{% stepper %}
{% step %}
**Get the item**

Use `/giveitem yourid meteo_whiteboard 1`, or grab it from the admin menu.
{% endstep %}

{% step %}
**Place it**

Use the item from your inventory. Aim where you want it and place with LMB (left mouse button). Use RMB to cancel and scroll up/down to rotate.
{% endstep %}

{% step %}
**Set the content**

Target the board and open "Manage Whiteboard". Pick a content type and paste a URL:

* **Video** - direct video files (mp4, webm, ogg, mov, m4v)
* **Image** - direct image files (png, jpg, gif, webp, ...)

Content is synced, so everyone near the board sees the same thing at the same time.
{% endstep %}

{% step %}
**Volume and clearing**

From the manage menu you can set the board volume, mute or unmute audio for everyone, and clear the screen. Only the owner of the board (or an admin) can change its content. Target the board and pick it up to return the item to your inventory.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
By default only trusted hosts are allowed for direct video and image links (Fivemanage, Streamable, Imgur, Discord CDN, GitHub and a few more).
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Render distance, allowed content types, allowed domains, default volume and the resync interval are all configurable in our config. You can change them once you get the package. We will guide you :)
{% endhint %}
