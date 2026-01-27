---
description: >-
  Installation guide for Meteo Studios Remote deployable spike strip system. You
  must carefully follow all the steps that you will see in this installation
  guide.
---

# Meteo Remote spikes

{% stepper %}
{% step %}
### Download the Script

* Visit [Cfx Portal](https://portal.cfx.re/)
* Login and go to assets tab
* Find **"Meteo Studios Remote spikes"** and download it
{% endstep %}

{% step %}
### Install the Files&#xD;

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your `server.cfg` file
* Add this line: `ensure [meteostudios]`<br>
{% endstep %}

{% step %}
### Add Phone Items to Inventory

#### For QBOX



**Add Items:**

1. Go to `meteo-remotespikes/install/qbox/`
2. Open ox-items.md
3. Copy all items into your `ox_inventory/data/items.lua` file

**Add Images:**

Copy all images from `meteo-phone/install/images/` to `ox_inventory/web/images/`

#### For QBCore

**Add Items:**

1. Go to `meteo-remotespikes/install/qbcore/`
2. Open qbcore-items.md
3. Copy all items into your `qb-core/shared/items.lua` file

**Add Images:**

Copy all images from `meteo-remotespikes/install/images/` to `qb-inventory/html/images/`
{% endstep %}
{% endstepper %}

***

**Need Help?**

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
