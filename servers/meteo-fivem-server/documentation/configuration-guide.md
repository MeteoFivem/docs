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

## ox.cfg

A few ox settings are needed alongside `meteo.cfg`.

```
setr ox:locale "en"
set fivemanage:key "YOUR_KEY"
```

| Setting | Description |
| ------- | ----------- |
| `ox:locale` | Sets the server language for all meteo scripts - see [How to Translate the Server](how-to/how-to-translate.md) for all supported language codes |
| `fivemanage:key` | Required only if `meteo:logger` is set to `oxlib` - get your key from <a href="https://fivemanage.com/" target="_blank">fivemanage.com</a> |

***

## server.cfg

Only change these specific lines in `server.cfg` - everything else should stay as is.

```
sv_licenseKey "YOUR_LICENSE_KEY"
sv_maxclients 8
sets tags "your, server, tags"
sv_hostname "Your Server Name"
sets sv_projectName "Your Server Name"
sets sv_projectDesc "Your server description here"
sets locale "en-US"
set mysql_connection_string "mysql://root@localhost/meteoserver?charset=utf8mb4"
```

| Setting | Description |
| ------- | ----------- |
| `sv_licenseKey` | Your server license key from <a href="https://portal.cfx.re/" target="_blank">portal.cfx.re</a> - required to run the server |
| `sv_maxclients` | Max player slots. Keep at `8` to stream custom clothing for free. If you need more than 8 slots, you need **Argentum** or higher subscription from <a href="https://portal.cfx.re/subscriptions" target="_blank">portal.cfx.re/subscriptions</a> |
| `sets tags` | Tags shown on the FiveM server list - helps players find your server |
| `sv_hostname` | Server name shown in the server browser |
| `sets sv_projectName` | Project name shown on the FiveM server list |
| `sets sv_projectDesc` | Short description shown on the FiveM server list |
| `sets locale` | Sets the country flag shown on the FiveM server list (e.g. `en-US`, `de-DE`, `fr-FR`, `tr-TR`) |
| `mysql_connection_string` | Database connection string. If you are on a **Windows VPS**, no need to change this - follow the installation guide instead. |

{% hint style="warning" %}
Do not modify anything below the `## DO NOT MODIFY BELOW` comment in `server.cfg`. Only change the settings listed above.
{% endhint %}

***

## permissions.cfg

Admin permissions are set in `permissions.cfg`. Use `group.admin` for the server owner and `qbcore.admin` for staff admins.

```
add_principal identifier.license:YOUR_LICENSE_HERE group.admin
add_principal identifier.discord:YOUR_DISCORD_ID qbcore.admin
```

See the full guide: [How to Add Admins](how-to/how-to-add-admins.md)

***

## meteo.cfg

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

The phone uses a few external API keys. Not all of them are required - it depends on which features you want to use. Set them in `meteo.cfg`:

```
set meteo:phone_fivemanage_token "YOUR_TOKEN"
set meteo:phone_gemini_key "YOUR_KEY"
set meteo:phone_openrouter_key "YOUR_KEY"
set meteo:phone_cf_turn_token_id "YOUR_TOKEN_ID"
set meteo:phone_cf_turn_api_token "YOUR_API_TOKEN"
```

| Setting | Required? | Used For | Where to Get It |
| ------- | --------- | -------- | --------------- |
| `meteo:phone_fivemanage_token` | Recommended | Gallery and camera image hosting | Go to <a href="https://fivemanage.com/" target="_blank">fivemanage.com</a>, create an account and generate an **image API key** (NOT the log API key - there are two types, make sure to pick image) |
| `meteo:phone_gemini_key` | Only for AI | Default AI provider for Ask iFruit. If not set, console shows a warning and the Ask iFruit app will not work | Go to <a href="https://aistudio.google.com/app/apikey" target="_blank">aistudio.google.com</a> and generate a free API key |
| `meteo:phone_openrouter_key` | Optional | Alternative AI provider for Ask iFruit. Only needed if you want to use OpenRouter instead of or alongside Gemini | Go to <a href="https://openrouter.ai/" target="_blank">openrouter.ai</a>, create an account and generate an API key |
| `meteo:phone_cf_turn_token_id` | Required for video calls | Video calling via WebRTC. Without this, video calls will not work | Follow the [Cloudflare TURN setup guide](how-to/how-to-cloudflare-turn.md) and copy the Token ID |
| `meteo:phone_cf_turn_api_token` | Required for video calls | Video calling via WebRTC. Without this, video calls will not work | Same TURN token from the [setup guide](how-to/how-to-cloudflare-turn.md) - copy the API Token |

{% hint style="info" %}
Need more help with any of these? Contact us on our <a href="https://discord.meteofivem.net" target="_blank">Discord</a> and we will help you set it up.
{% endhint %}
