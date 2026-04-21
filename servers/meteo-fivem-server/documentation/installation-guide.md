---
description: >-
  Step-by-step installation guide for the meteo fivem server on Windows.
  Everything you need to get your server running from scratch.
icon: download
---

# Installation Guide

{% hint style="info" %}
Make sure to check the **exclusive installation video** in the customer section on our <a href="https://discord.meteofivem.net" target="_blank">Discord server</a> - it walks through everything visually and is the easiest way to follow along.
{% endhint %}

***

## Windows Installation

### What You Need

Before starting, make sure you have purchased and downloaded the server package.

* Purchase at <a href="https://meteofivem.net/meteo-fivem-server" target="_blank">meteofivem.net/meteo-fivem-server</a>
* Download your server files from the customer section on <a href="https://meteofivem.net" target="_blank">meteofivem.net</a>

***

### Step 1 - Download The Tools

Download and install all of these before continuing:

| Tool | What it's for | Download |
| ---- | ------------- | -------- |
| **WinRAR** | Extracting server files | <a href="https://www.rarlab.com/download.htm" target="_blank">rarlab.com</a> |
| **FiveM Artifacts** | The FiveM server build | <a href="https://artifacts.jgscripts.com/" target="_blank">artifacts.jgscripts.com</a> - download the latest build with no reported issues |
| **VS Code** | Editing config files | <a href="https://code.visualstudio.com/" target="_blank">code.visualstudio.com</a> |
| **MariaDB** | Database server | <a href="https://mariadb.org/download" target="_blank">mariadb.org/download</a> |
| **HeidiSQL** | Database management | <a href="https://www.heidisql.com/download.php" target="_blank">heidisql.com/download.php</a> |

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
**Run the database files in order**

Go to your meteo server folder and find the database folder. You will see two `.sql` files. The order matters.

1. Open `meteoserver.sql` in HeidiSQL and run it first. This creates the `meteoserver` database and all the required tables.
2. Then open `meteoserverdata.sql` and run it. This fills the tables with all the starter data (items, locations, configs etc).

{% hint style="warning" %}
If you want to rename the database from `meteoserver` to something else, you must change it in **both** files or the second file will fail.

In `meteoserver.sql` update these two lines at the top:

```sql
CREATE DATABASE IF NOT EXISTS `meteoserver` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci */;
USE `meteoserver`;
```

In `meteoserverdata.sql` update this line at the top:

```sql
USE `meteoserver`;
```

Replace `meteoserver` with your custom database name in all three places. And make sure your `mysql_connection_string` in `server.cfg` matches.
{% endhint %}

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

Log into your FiveM account at <a href="https://portal.cfx.re/" target="_blank">portal.cfx.re</a> and generate a server license key.
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
