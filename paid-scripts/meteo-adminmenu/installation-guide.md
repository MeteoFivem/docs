---
description: >-
  Installation guide for Meteo Admin Menu. Follow all steps carefully to ensure
  proper setup on your server.
---

# Installation guide

{% hint style="info" %}
Purchase This Script from: <a href="https://meteo.tebex.io/" target="_blank">Meteo Admin Menu</a>
{% endhint %}

{% stepper %}
{% step %}
**Download the Resource**

* Visit <a href="https://portal.cfx.re/" target="_blank">Cfx Portal</a>
* Login and go to assets tab
* Find **"Meteo Studios Admin Menu"** and download it
{% endstep %}

{% step %}
**Install the Files**

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your **server.cfg** file
* If you already have `ensure [meteostudios]`, the script will load with the bundle
* Otherwise add: `ensure meteo-adminmenu`
{% endstep %}

{% step %}
**Install Required Resources**

Download and update these resources (get the latest versions)

* <a href="https://github.com/overextended/ox_lib/releases" target="_blank">ox\_lib</a> - Required for callbacks, locale, and UI
* <a href="https://github.com/overextended/oxmysql/releases" target="_blank">oxmysql</a> - Required for database queries
* <a href="https://github.com/MeteoStudios/meteo-keybinddisplay" target="_blank">meteo-keybinddisplay</a> - Required for the on-screen keybind hint shown while spectating

{% hint style="warning" %}
**meteo-keybinddisplay is required.** Without it, the Backspace exit hint while spectating will not appear. Make sure it is installed and ensured before meteo-adminmenu.
{% endhint %}

Make sure they're all added in your server.cfg before meteo-adminmenu:

```
ensure ox_lib
ensure oxmysql
ensure meteo-keybinddisplay
ensure [meteostudios]
```

If you do not use the `[meteostudios]` bundle folder:

```
ensure ox_lib
ensure oxmysql
ensure meteo-keybinddisplay
ensure meteo-adminmenu
```
{% endstep %}

{% step %}
**Setup Database**

* Open **HeidiSQL**
* Find the file: `meteo-adminmenu/install/meteo_admin.sql`
* Run this SQL file in your database

This creates the tables required for admin logs and related data.
{% endstep %}

{% step %}
**Remove Old Admin Menu Scripts**

{% hint style="warning" %}
**Important:** You must remove your existing admin menu scripts to avoid command and keybind conflicts.
{% endhint %}

**Common scripts to remove:**

| Script           | Action                                |
| ---------------- | ------------------------------------- |
| `qb-adminmenu`   | Delete folder                         |
| `qbx_adminmenu`  | Delete folder                         |

**Steps:**

1. Stop your server
2. Delete the old admin menu folder from your resources
3. Remove the `ensure` line from your **server.cfg**
4. Start your server with meteo-adminmenu
{% endstep %}

{% step %}
**Grant Admin Permissions**

Admins are recognized through QBCore permissions or ace principals. Both work:

**Via QBCore command:**

```
/setpermissions [id] admin
/setpermissions [id] god
```

**Via ace principals in `permissions.cfg` (QBCore):**

```
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.admin
add_principal identifier.discord:123456789012345678 group.admin
```

Make sure your `permissions.cfg` already has the QBCore group aces (`add_ace group.admin qbcore.admin allow`, etc.) loaded before any `add_principal` lines.

**Via ace principals in `permissions.cfg` (QBox):**

QBox uses a slightly different ace setup. The default QBox `permissions.cfg` already wires up `group.admin`, `group.mod`, and `group.support` with inheritance, so you only need to add the principal line:

```
add_principal identifier.license:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx group.admin
add_principal identifier.discord:123456789012345678 group.admin
```

Reference (already present in default QBox `permissions.cfg`):

```
add_ace group.admin command allow
add_ace group.admin admin allow
add_ace group.mod mod allow
add_ace group.support support allow

add_principal group.admin group.mod
add_principal group.mod group.support
```
{% endstep %}

{% step %}
**Configure the Script**

1. Open `meteo-adminmenu/shared/config.lua`
2. Set `Config.Framework`, `Config.Inventory`, and `Config.Clothing` to match your server (or leave on `auto`)
3. Adjust `Config.MoneyLimits` to your server's economy
4. Set `Config.ServerInfo` (name, Discord) - shown in the menu
5. Configure `Config.VehicleCustomization.menuEvent` if you use a custom mod menu
6. Adjust `Config.Keybinds` defaults if needed
{% endstep %}
{% endstepper %}

***

## Quick Checklist

* Downloaded from Cfx Portal
* Installed in `[meteostudios]` folder (or ensured directly as `meteo-adminmenu`)
* Added to server.cfg
* Installed ox\_lib, oxmysql, meteo-keybinddisplay
* Ran `install/meteo_admin.sql` in database
* Removed old admin menu script
* Granted admin permissions to staff
* Configured `shared/config.lua`

***

## Next Steps

Now the installation is complete. Open the menu in-game with `F9` (or `/admin`) and start using it.

* [Useful Commands](useful-commands.md) - Admin commands reference
* [Changelogs](changelogs.md) - Version history

***

## Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
