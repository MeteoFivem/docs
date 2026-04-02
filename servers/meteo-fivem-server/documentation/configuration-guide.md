---
description: >-
  Complete configuration guide for the meteo fivem server. All settings
  explained in one place - customize your server name, currency, language,
  Discord rich presence and more.
icon: sliders
---

# Configuration Guide

All meteo server settings are controlled from a single file: `meteo.cfg`. Add it to your server config and customize everything from one place.

{% hint style="info" %}
All settings use `setr` (replicated to clients) or `set` (server-side only) as shown below.
{% endhint %}

***

## Meteo CFG Guide

### Server Settings

These control the core identity and behavior of your server across all meteo scripts.

```
setr meteo:name "Meteo Server"
setr meteo:logo "https://your-logo-url.png"
setr meteo:currency "$"
setr meteo:logger "oxlib"
setr meteo:speedunit "mph"
setr meteo:groupmaxMembers 4
```

| Setting | Description |
| ------- | ----------- |
| `meteo:name` | Display name shown across all meteo UIs (HUD, phone, tablet, etc.) |
| `meteo:logo` | URL to your server logo image - shown in menus and loading screens |
| `meteo:currency` | Currency symbol shown in shops, menus and HUDs - use `$`, `€`, `£` or any symbol |
| `meteo:logger` | Log backend - `discord` sends logs to a webhook, `oxlib` logs to server console |
| `meteo:speedunit` | Speed unit in HUD and police radar - `mph` or `kmh` |
| `meteo:groupmaxMembers` | Max players allowed in a group for crime activities and civilian jobs |

***

### Discord Rich Presence

Controls what players see in Discord when they are on your server. For full setup instructions see the [How to Change Discord RPC](how-to/how-to-discord-rpc.md) guide.

```
set meteo:discord_enabled true
set meteo:discord_player_count true
set meteo:discord_app_id "your_app_id"
set meteo:discord_icon_large "your_large_icon_key"
set meteo:discord_icon_small "your_small_icon_key"
```

| Setting | Description |
| ------- | ----------- |
| `meteo:discord_enabled` | Enable or disable Discord rich presence entirely - `true` or `false` |
| `meteo:discord_player_count` | Show live player count in Discord status - `true` or `false` |
| `meteo:discord_app_id` | Your Discord application ID - get this from the Discord Developer Portal |
| `meteo:discord_icon_large` | Key name of the large icon uploaded to your Discord app's Rich Presence assets |
| `meteo:discord_icon_small` | Key name of the small icon uploaded to your Discord app's Rich Presence assets |

{% content-ref url="how-to/how-to-discord-rpc.md" %}
[How to Change Discord RPC](how-to/how-to-discord-rpc.md)
{% endcontent-ref %}

***

### Meteo Phone - API Keys

Phone API keys are configured separately. See the full guide here:

{% content-ref url="../../../paid-scripts/meteo-phone/configuration-guide/" %}
[Meteo Phone - Configuration Guide](../../../paid-scripts/meteo-phone/configuration-guide/)
{% endcontent-ref %}
