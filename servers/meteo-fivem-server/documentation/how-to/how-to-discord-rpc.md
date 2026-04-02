---
description: >-
  How to set up and customize Discord rich presence for your meteo fivem server.
  Change the app name, icons and player count display shown in Discord.
icon: discord
---

# How to Change Discord RPC

Discord Rich Presence (RPC) lets your players show they are playing on your server directly in their Discord status. You can fully customize the app name, icons and what information is displayed.

***

## What You Need

* A Discord account
* Access to the [Discord Developer Portal](https://discord.com/developers/applications)
* Your `meteo.cfg` file

***

## Setting Up Your Discord App

{% stepper %}
{% step %}
**Create a Discord application**

Go to [discord.com/developers/applications](https://discord.com/developers/applications) and click **New Application**. Give it your server name (e.g. "My FiveM Server"). This is the name players will see in their Discord status.
{% endstep %}

{% step %}
**Copy your Application ID**

On the application's **General Information** page, copy the **Application ID**. You will need this for `meteo:discord_app_id`.
{% endstep %}

{% step %}
**Upload your icons**

Go to **Rich Presence → Art Assets** in your Discord app. Upload your server logo images here. Give each one a key name (e.g. `server_logo_large`, `server_logo_small`). These key names are what you use in `meteo:discord_icon_large` and `meteo:discord_icon_small`.

{% hint style="info" %}
Recommended icon size is 1024x1024px. Icons must be approved by Discord before they show up - this usually takes a few minutes.
{% endhint %}
{% endstep %}

{% step %}
**Update your meteo.cfg**

Add your values to `meteo.cfg`:

```
set meteo:discord_enabled true
set meteo:discord_player_count true
set meteo:discord_app_id "YOUR_APPLICATION_ID"
set meteo:discord_icon_large "server_logo_large"
set meteo:discord_icon_small "server_logo_small"
```

Replace the values with your actual application ID and icon key names.
{% endstep %}

{% step %}
**Restart your server**

Save `meteo.cfg` and restart your server. Players will now see your custom Discord rich presence when they join.
{% endstep %}
{% endstepper %}

***

## Settings Reference

| Setting | Description |
| ------- | ----------- |
| `meteo:discord_enabled` | Set to `false` to disable Discord RPC entirely |
| `meteo:discord_player_count` | Set to `false` to hide player count from the Discord status |
| `meteo:discord_app_id` | The Application ID from your Discord Developer Portal app |
| `meteo:discord_icon_large` | Key name of the large icon in your app's Rich Presence Art Assets |
| `meteo:discord_icon_small` | Key name of the small icon in your app's Rich Presence Art Assets |

***

{% hint style="success" %}
Once set up, every player on your server will automatically show your server name and icons in their Discord status with no extra setup needed on their end.
{% endhint %}
