---
description: >-
  Host meteo-appearance clothing images on Fivemanage so players do not download
  them on connect.
icon: cloud-arrow-up
---

# How to Use Fivemanage for Clothing Images

This guide walks you through moving the `meteo-appearance` clothing images off your server and onto a Fivemanage CDN. Once set up, players no longer download all the clothing images when they connect - the images only load from Fivemanage when a player opens the clothing menu.

This same idea works for any meteo script that ships with a large image folder, but this guide uses `meteo-appearance` as the example.

***

{% hint style="info" %}
**Why do this?** The clothing images folder is large. By default every player downloads all of it on connect, which slows down their join time. Hosting them on a CDN removes that download and only fetches an image when it is actually needed.
{% endhint %}

{% hint style="warning" %}
**Read before you continue:**

* You must **remove the local images folder from the resource** after uploading. If you leave it in place, players will still download the images on connect and the CDN does nothing.
* Keep a backup of the images folder somewhere outside the resource before deleting it.
{% endhint %}

***

## What You Need

* A Fivemanage account (free to create)
* The `meteo-appearance` resource in your server
* About 5 minutes

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
**Upload the clothing images**

Open the `meteo-appearance/web/build/images/clothing` folder in your resource and upload all of the images into the `clothing` folder you just created on Fivemanage.
{% endstep %}

{% step %}
**Set the CDN URL in config**

Copy the URL of the `clothing` folder from Fivemanage. Open `meteo-appearance/shared/config.lua`, find `Config.clothingImagesCDN`, paste the URL there, and save the file.
{% endstep %}

{% step %}
**Remove the local images folder**

Delete the `meteo-appearance/web/build/images/clothing` folder, or move it somewhere outside the resource and keep it as a backup.

{% hint style="danger" %}
This step is required. If the images folder stays inside the resource, players will still download all of it when they connect and the CDN setup will have no effect.
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
