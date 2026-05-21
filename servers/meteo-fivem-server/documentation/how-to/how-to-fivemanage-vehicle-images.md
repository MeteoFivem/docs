---
description: >-
  Capture meteo-dealerships vehicle images and host them on Fivemanage so
  players do not download them on connect.
icon: cloud-arrow-up
---

# How to Use Fivemanage for Vehicle Images

This guide walks you through capturing the `meteo-dealerships` vehicle images with the `meteo-vehiclecapture` tool and hosting them on a Fivemanage CDN. Once set up, players no longer download all the vehicle images when they connect - the images only load from Fivemanage when a player opens a dealership.

This same idea works for any meteo script that uses a large image folder, but this guide uses `meteo-dealerships` as the example.

***

{% hint style="info" %}
**Why do this?** The vehicle images are large. Hosting them on a CDN keeps them off your server download, so players join faster and an image is only fetched from Fivemanage when it is actually needed.
{% endhint %}

{% hint style="warning" %}
**Read before you continue:**

* `meteo-vehiclecapture` is a capture tool only. Remove it from your server once you are done - it is not meant to run on a live server.
* Capture your images on a server that already has all of your vehicles (including any custom vehicles) loaded, so the captured images match what players see.
{% endhint %}

***

## What You Need

* A Fivemanage account (free to create)
* The `meteo-vehiclecapture` tool: <a href="https://github.com/MeteoStudios/meteo-vehiclecapture" target="_blank">github.com/MeteoStudios/meteo-vehiclecapture</a>
* The `meteo-dealerships` resource in your server
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
**Create a vehicles folder in storage**

In the Fivemanage dashboard, go to **Storage** and create a new folder called `vehicles`.
{% endstep %}

{% step %}
**Download meteo-vehiclecapture**

Download the capture tool from <a href="https://github.com/MeteoStudios/meteo-vehiclecapture" target="_blank">github.com/MeteoStudios/meteo-vehiclecapture</a> and add it to your server resources.
{% endstep %}

{% step %}
**Capture the in-game images**

Start the server with `meteo-vehiclecapture` and use it to capture the vehicle images in-game. When it finishes, the images are saved into the tool's `images/vehicles` folder.
{% endstep %}

{% step %}
**Upload the captured images**

Open the `meteo-vehiclecapture/images/vehicles` folder and upload all of the images into the `vehicles` folder you created on Fivemanage.
{% endstep %}

{% step %}
**Set the CDN URL in config**

Copy the URL of the `vehicles` folder from Fivemanage. Open `meteo-dealerships/shared/config.lua`, find `Config.imagesCDN`, paste the URL there, and save the file.
{% endstep %}

{% step %}
**Delete meteo-vehiclecapture**

Remove the `meteo-vehiclecapture` resource from your server. It is only needed for the capture step and should not run on a live server.

{% hint style="danger" %}
Do not leave `meteo-vehiclecapture` on your live server. It is a one-time capture tool, not a runtime resource.
{% endhint %}
{% endstep %}

{% step %}
**Restart the resource**

Restart `meteo-dealerships` (or your server). Vehicle images now load from Fivemanage only when a player opens a dealership.
{% endstep %}
{% endstepper %}

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
