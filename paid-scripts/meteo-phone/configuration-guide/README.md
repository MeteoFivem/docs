---
description: Configuration guide for Meteo Studios FiveM Phone
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/hPLkuIrL5TffIt3aasi9/paid-scripts/meteo-phone/configuration-guide
---

# Configuration guide

{% hint style="warning" %}
**Updating from an older version?** API keys are no longer set inside `server/sv_api.lua`. They now live in your `server.cfg` (or any `.cfg` file you load) as convars. Follow Step 1 below to migrate, then delete the old key values from `sv_api.lua` if you still have them there.
{% endhint %}

***

### Step 1: Setup API Keys (server.cfg)

All API keys for meteo-phone are configured through convars in your `server.cfg`. This keeps secrets out of the resource files and makes updates much easier (your keys won't get overwritten when you replace the script).

#### 1. Paste this block into your `server.cfg`

Add the following block anywhere in your `server.cfg` (or any `.cfg` you load with `exec`). Make sure it loads **before** `ensure meteo-phone`.

```cfg
# -----------------------------------------------
# Meteo Phone - API Keys
# -----------------------------------------------

set meteo:phone_fivemanage_token "YOUR_KEY_HERE"
set meteo:phone_gemini_key "YOUR_KEY_HERE"
set meteo:phone_openrouter_key "YOUR_KEY_HERE"
set meteo:phone_cf_turn_token_id "YOUR_KEY_HERE"
set meteo:phone_cf_turn_api_token "YOUR_KEY_HERE"
```

Then replace each `YOUR_KEY_HERE` with the matching key from the sections below. Leave any you don't use as `YOUR_KEY_HERE` (the feature will just stay disabled, the rest of the phone will work fine).

***

#### 2. FiveManage (Gallery + Camera)

**Used for:** uploading photos from the Gallery and Camera apps.

1. Visit <a href="https://fivemanage.com/" target="_blank">fivemanage.com</a> and create an account
2. Generate an API key
3. Paste it into `meteo:phone_fivemanage_token`

***

#### 3. Google Gemini (Ask iFruit AI)

**Used for:** the Ask iFruit AI assistant.

1. Get a key from <a href="https://aistudio.google.com/app/apikey" target="_blank">aistudio.google.com/app/apikey</a>
2. Paste it into `meteo:phone_gemini_key`

***

#### 4. OpenRouter (optional AI fallback)

**Used for:** alternate AI model routing if you choose to use it.

1. Get a key from <a href="https://openrouter.ai/keys" target="_blank">openrouter.ai/keys</a>
2. Paste it into `meteo:phone_openrouter_key`

You can leave this as `YOUR_KEY_HERE` if you only want to use Gemini.

***

#### 5. Cloudflare TURN (Video Calls)

**Used for:** WebRTC video calling.

1. Create a Cloudflare account if you don't have one
2. Open <a href="https://dash.cloudflare.com/?to=/:account/realtime/turn/overview" target="_blank">Realtime &#x2192; TURN Server</a> in the Cloudflare dashboard
3. Press **Create**, give it any name (for example `meteo-phone`), press **Create** again
4. Copy the **Turn Token ID** into `meteo:phone_cf_turn_token_id`
5. Copy the **API Token** into `meteo:phone_cf_turn_api_token`

{% hint style="info" %}
Without this, video calls will still try to connect but quality will be unreliable for players on stricter networks.
{% endhint %}

***

### Step 2: Setup Discord Logs (Optional)

Go to `meteo-phone/server/sv_logs.lua`

1. Enable logging if you want to track phone activities
2. Add your Discord webhook URL:

```lua
webhook = "YOUR_DISCORD_WEBHOOK_URL_HERE"
```

***

### Step 3: Configure Phone Slot

Go to `meteo-phone/shared/config.lua`

Find the `Config.phoneSlot` setting and set which inventory slot the phone must be in to open.

**Example:**

```lua
Config.phoneSlot = 1  -- Phone must be in slot 1 to open
```

***

### Step 4: Language/Translations (Optional)

If you need translations:

1. Go to `meteo-phone/shared/config.lua`
2. Uncomment the `lib.locale('')` part
3. Put your language key inside (example: `'en'`, `'es'`, `'fr'`)
4. Make sure your language file exists in the `locales/` folder
5. If it doesn't exist, create a new `.json` file with your language

**Need help with translations?** Join our Discord: <a href="http://discord.meteofivem.net/" target="_blank">http://discord.meteofivem.net/</a>

***

### You're All Set!

**Restart your server** and the Meteo Phone should be working!

***

**Need Help?**

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
