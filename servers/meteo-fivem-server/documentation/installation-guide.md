---
description: >-
  Step-by-step installation guide for the meteo fivem server on Windows.
  Everything you need to get your server running from scratch.
icon: download
---

# Installation Guide

{% hint style="info" %}
Make sure to check the **exclusive installation video** in the customer section on our [Discord server](https://discord.meteofivem.net) - it walks through everything visually and is the easiest way to follow along.
{% endhint %}

***

## Windows Installation

### What You Need

Before starting, make sure you have purchased and downloaded the server package.

* Purchase at [meteofivem.net/meteo-fivem-server](https://meteofivem.net/meteo-fivem-server)
* Download your server files from the customer section on [meteofivem.net](https://meteofivem.net)

***

### Step 1 - Download The Tools

Download and install all of these before continuing:

| Tool | What it's for | Download |
| ---- | ------------- | -------- |
| **WinRAR** | Extracting server files | [rarlab.com](https://www.rarlab.com/download.htm) |
| **FiveM Artifacts** | The FiveM server build | [artifacts.jgscripts.com](https://artifacts.jgscripts.com/) - download the latest build with no reported issues |
| **VS Code** | Editing config files | [code.visualstudio.com](https://code.visualstudio.com/) |
| **MariaDB** | Database server | [mariadb.org/download](https://mariadb.org/download) |
| **HeidiSQL** | Database management | [heidisql.com/download.php](https://www.heidisql.com/download.php) |

***

### Step 2 - Extract Server Files

{% stepper %}
{% step %}
**Extract the meteo server package**

Right click the downloaded server package → **Extract here** using WinRAR. Place it in a folder where you want to run your server from.
{% endstep %}

{% step %}
**Extract FiveM artifacts**

Inside the server files you will find a folder named `fivem-data`. Extract the FiveM artifacts you downloaded into that folder.
{% endstep %}
{% endstepper %}

***

### Step 3 - Install The Tools

{% stepper %}
{% step %}
**Install VS Code**

Run the VS Code installer and complete the setup. You will use this to edit your config files.
{% endstep %}

{% step %}
**Install MariaDB**

Run the MariaDB installer. During setup, set a root password and remember it - you will need it for HeidiSQL.
{% endstep %}

{% step %}
**Install HeidiSQL**

Run the HeidiSQL installer and complete the setup.
{% endstep %}
{% endstepper %}

***

### Step 4 - Set Up The Database

{% stepper %}
{% step %}
**Open HeidiSQL**

Open HeidiSQL and create a new connection using your MariaDB root credentials.
{% endstep %}

{% step %}
**Run the database file**

Go to your meteo server folder, find the database folder and open the `.sql` file using HeidiSQL. Run it - this will automatically create the meteo server database with all the required tables.

{% hint style="info" %}
If you are not sure about this step, refer to the exclusive installation video in the customer section on our Discord - it shows exactly how to do this.
{% endhint %}
{% endstep %}
{% endstepper %}

***

### Step 5 - Add Your Server License Key

{% stepper %}
{% step %}
**Get your license key**

Log into your FiveM account at [portal.cfx.re](https://portal.cfx.re/) and generate a server license key.
{% endstep %}

{% step %}
**Add it to server.cfg**

Open `server.cfg` in VS Code and add your license key:

```
sv_licenseKey "YOUR_LICENSE_KEY_HERE"
```
{% endstep %}
{% endstepper %}

***

### Step 6 - Start The Server And Configure txAdmin

{% stepper %}
{% step %}
**Start the server**

Run the server start file. Your browser should automatically open the txAdmin setup page.
{% endstep %}

{% step %}
**Configure txAdmin**

Follow the txAdmin setup wizard. Point it to your server folder and complete the setup.
{% endstep %}

{% step %}
**That's it**

Your server is now running. Head over to the configuration guide to finish setting everything up.
{% endstep %}
{% endstepper %}

***

## Next Step - Configure Your Server

Now that the server is running, configure it to your needs.

{% content-ref url="configuration-guide.md" %}
[Configuration Guide](configuration-guide.md) - Set up meteo.cfg, server.cfg, permissions and more
{% endcontent-ref %}
