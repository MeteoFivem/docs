---
description: >-
  Installation guide for Meteo Studios FiveM Walkable Apartments. You must
  carefully follow all the steps that you will see in this installation guide.
---

# Installation guide

{% hint style="info" %}
Purchase This Script from: [Meteo FiveM Walkable Apartments](https://meteo.tebex.io/package/7258443)
{% endhint %}

{% stepper %}
{% step %}
#### Download Meteo Walkable Apartments

* Visit [Cfx Portal](https://portal.cfx.re/)
* Login and go to assets tab
* Find **"Meteo Studios Apartments"** and download it
{% endstep %}

{% step %}
#### Install the Files

* Unzip the downloaded file (`meteo-apartments-bundle`)
* You'll see two folders: `meteo-apartments` and `meteo-furnishing`
* Create a folder called `[meteostudios]` in your resources (if you don't have one)
* Inside `[meteostudios]`, create a folder called `[apartments]` to organize apartment resources
* Put both `meteo-apartments` and `meteo-furnishing` inside `[meteostudios]/[apartments]/`
* Open your **server.cfg** file
* Add this line: `ensure [meteostudios]`

Your folder structure should look like:

```
resources/
  [meteostudios]/
    [apartments]/
      meteo-apartments/
      meteo-furnishing/
```

{% hint style="warning" %}
**Folder structure matters.** This organization keeps your server clean and makes managing meteo studios fivem script updates easier.
{% endhint %}
{% endstep %}

{% step %}
#### Install WiWang Hotel MLO (Free)

Meteo Apartments comes pre-configured with the WiWang Hotel MLO (380 rooms) by FL0KY. (Note: we only pre configured for 210 rooms (11 floors). you can create more rooms using our [built in apartments](for-developers/creating-rooms.md) creator easily)

**Download the MLO:**

1. Download from: [https://github.com/uFLOKY/wiwang\_hotel](https://github.com/uFLOKY/wiwang_hotel)
2. Unzip the downloaded file
3. Inside `wiwang_hotel-main` folder, find `map_wiwang_hotel`
4. Copy `map_wiwang_hotel` to `[meteostudios]/[apartments]/`

**Remove Built-in Elevators:**

The MLO includes elevator code, but Meteo Apartments has its own elevator system built-in.

1. Open `map_wiwang_hotel/fxmanifest.lua`
2. Delete this line: `client_script 'elevators.lua'`
3. Delete the file: `map_wiwang_hotel/elevators.lua`

Your folder structure should look like:

```
resources/
  [meteostudios]/
    [apartments]/
      meteo-apartments/
      map_wiwang_hotel/
```

{% hint style="success" %}
**Free MLO with 380 rooms.** This is a massive apartment complex ready to use out of the box. Original MLO by FL0KY: [Forum Post](https://forum.cfx.re/t/mlo-wiwang-hotel-380-rooms/5364084)
{% endhint %}
{% endstep %}

{% step %}
#### Install Required Resources

Download and install these resources (get the latest versions)

| Resource           | Why You Need It                 |
| ------------------ | ------------------------------- |
| **ox\_lib**        | Modern UI menus and callbacks   |
| **oxmysql**        | Database queries                |
| **interact-sound** | Door sounds and doorbell system |

**interact-sound Installation:**

1. Download from: [https://github.com/Qbox-project/interact-sound](https://github.com/Qbox-project/interact-sound)
2. Place in your resources folder
3. Add to server.cfg: `ensure interact-sound`

Make sure all dependencies are added to your server.cfg **before** meteo-apartments.
{% endstep %}

{% step %}
#### Setup Database

* Open **HeidiSQL** (or your database tool)
* Find the file: `meteo-apartments/install/meteo_apartments.sql`
* Run this SQL file in your database

This creates the tables needed for apartment ownership, members, and logs.
{% endstep %}

{% step %}
#### Add Sounds to interact-sound

Door locks and doorbells need sound files.

1. Go to `meteo-apartments/install/sounds/`
2. Copy all sound files
3. Paste them into `interact-sound/client/html/sounds/`

The sounds include door lock clicks and doorbell chimes.
{% endstep %}

{% step %}
#### Configure for Your Server

Go to `meteo-apartments/shared/config.lua` and configure based on your server setup.

**You might need to configure:**

* Radial menu system (if you use one)
* Doorlock settings (security levels, lockpick difficulty)
* Apartment prices and room types

{% hint style="info" %}
**Compatibility configuration is important.** We'll cover all compatibility options in detail in the Configuration Guide.
{% endhint %}

We'll add a detailed compatibility guide link here soon.
{% endstep %}
{% endstepper %}

***

### Quick Checklist

* Installed in `[meteostudios]/[apartments]/` folder
* Added to server.cfg
* Installed all dependencies (ox\_lib, oxmysql, interact-sound)
* Ran SQL file
* Added sounds to interact-sound
* Configured compatibility settings

***

### Next Steps

Now that installation is complete, check the **Configuration Guide** for detailed setup instructions. [**Configuration Guide**](https://sample-url-here/configuration-guide)



**What you'll find in the Configuration Guide:**

* QBX Integration (garages, starter apartments)
* Adding new apartment complexes and rooms
* Language/translation setup
* Furniture limits and upgrades
* Security levels and doorlock configuration
* Lockpicking and police raid settings
* Apartment pricing configuration

***

**Need Help?**

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
