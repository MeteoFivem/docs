---
description: >-
  Capture meteo-appearance clothing images and host them on Fivemanage so
  players do not download them on connect.
icon: cloud-arrow-up
---

# How to Use Fivemanage for Clothing Images

This guide walks you through capturing the `meteo-appearance` clothing images with the `meteo-clothingcapture` tool and hosting them on a Fivemanage CDN. Once set up, players no longer download all the clothing images when they connect - the images only load from Fivemanage when a player opens the clothing menu.

This same idea works for any meteo script that uses a large image folder, but this guide uses `meteo-appearance` as the example.

***

{% hint style="info" %}
**Why do this?** The clothing images are large. Hosting them on a CDN keeps them off your server download, so players join faster and an image is only fetched from Fivemanage when it is actually needed.
{% endhint %}

{% hint style="warning" %}
**Read before you continue:**

* `meteo-clothingcapture` is a capture tool only. Remove it from your server once you are done - it is not meant to run on a live server.
* Capture your images on a server that already has all of your clothing (including any custom clothing) loaded, so the captured images match what players see.
{% endhint %}

***

## What You Need

* A Fivemanage account (free to create)
* The `meteo-clothingcapture` tool: <a href="https://github.com/MeteoStudios/meteo-clothingcapture" target="_blank">github.com/MeteoStudios/meteo-clothingcapture</a>
* The `meteo-appearance` resource in your server
* About 10 minutes

***

## Video guide

<a href="https://www.youtube.com/@meteostudios/videos" target="_blank">Watch on YouTube</a>

***

## Steps

{% stepper %}
{% step %}
**Create a Fivemanage account**

Go to <a href="https://fivemanage.com" target="_blank">fivemanage.com</a>. If you do not have an account yet, create a new one.
{% endstep %}

{% step %}
**Create a clothing folder in storage**

In the Fivemanage dashboard, go to **Storage** and create a new folder called `clothing`.
{% endstep %}

{% step %}
**Download meteo-clothingcapture**

Download the capture tool from <a href="https://github.com/MeteoStudios/meteo-clothingcapture" target="_blank">github.com/MeteoStudios/meteo-clothingcapture</a> and add it to your server resources.
{% endstep %}

{% step %}
**Capture the in-game images**

Start the server with `meteo-clothingcapture` and use it to capture the clothing images in-game. When it finishes, the images are saved into the tool's `images/clothing` folder.
{% endstep %}

{% step %}
**Upload the captured images**

Open the `meteo-clothingcapture/images/clothing` folder and upload all of the images into the `clothing` folder you created on Fivemanage.
{% endstep %}

{% step %}
**Set the CDN URL in config**

Copy the URL of the `clothing` folder from Fivemanage. Open `meteo-appearance/shared/config.lua`, find `Config.clothingImagesCDN`, paste the URL there, and save the file.
{% endstep %}

{% step %}
**Delete meteo-clothingcapture**

Remove the `meteo-clothingcapture` resource from your server. It is only needed for the capture step and should not run on a live server.

{% hint style="danger" %}
Do not leave `meteo-clothingcapture` on your live server. It is a one-time capture tool, not a runtime resource.
{% endhint %}
{% endstep %}

{% step %}
**Restart the resource**

Restart `meteo-appearance` (or your server). Clothing images now load from Fivemanage only when a player opens the clothing menu.
{% endstep %}
{% endstepper %}

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
