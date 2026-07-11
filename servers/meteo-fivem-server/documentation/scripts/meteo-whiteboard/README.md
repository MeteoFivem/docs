---
description: >-
  Meteo whiteboard - placeable synced whiteboards that render YouTube, images
  and live streams, designed exclusively for the meteo fivem server.
---

# Meteo Whiteboard

This is a guide about testing the meteo fivem whiteboard script designed exclusively for meteo server. Place a board anywhere and play video, images, YouTube, Twitch or Kick streams on it, synced for everyone nearby.

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
* **YouTube** - a YouTube video link
* **Twitch** - a Twitch channel stream
* **Kick** - a Kick channel stream

Content is synced, so everyone near the board sees the same thing at the same time.
{% endstep %}

{% step %}
**Volume and clearing**

From the manage menu you can set the board volume, mute or unmute audio for everyone, and clear the screen. Only the owner can change a board's content. Target the board and pick it up to return the item to your inventory.
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
By default only trusted hosts are allowed for direct video and image links (Fivemanage, Streamable, Imgur, Discord CDN, GitHub and a few more). YouTube, Twitch and Kick carry their own ToS risk - you can turn any of these content types off in the config.
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Render distance, allowed content types, allowed domains, default volume and the resync interval are all configurable in our config. You can change them once you get the server. We will guide you :)
{% endhint %}
