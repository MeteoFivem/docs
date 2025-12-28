---
description: Configuration guide for Meteo Studios FiveM Phone
---

# Configuration guide

### Step 1: Setup API Keys

Go to `meteo-phone/server/sv_api.lua`

#### 1. FiveManage API (Image Hosting)

**Used for:** Gallery and Camera features

1. Visit: [https://fivemanage.com/](https://fivemanage.com/)
2. Create an account and get your API key
3. Update this line:

```lua
FIVEMANAGE_API_TOKEN = 'YOUR_FIVEMANAGE_API_KEY_HERE'
```

Replace `YOUR_FIVEMANAGE_API_KEY_HERE` with your actual API key

***

#### 2. Google Gemini API (AI Assistant)

**Used for:** Ask iFruit (AI assistant feature)

1. Get your API key from: [https://aistudio.google.com/app/apikey](https://aistudio.google.com/app/apikey)
2. Update this line:

```lua
GEMINI_API_KEY = 'YOUR_GEMINI_API_KEY_HERE'
```

Replace `YOUR_GEMINI_API_KEY_HERE` with your actual API key

***

#### 3. Cloudflare TURN (Video Calls)

**Used for:** Video calling feature via WebRTC

1. Visit: [https://dash.cloudflare.com/](https://dash.cloudflare.com/)
2. Go to **Calls > TURN**
3. Create a TURN token
4. Copy your **Token ID** and **API Token**
5. Update this section:

```lua
CLOUDFLARE_TURN = {
    TokenID = "YOUR_TOKEN_ID_HERE",
    APIToken = "YOUR_API_TOKEN_HERE",
}
```

**Important:** This is required for video calls! Without it, players will experience issues with video calling.

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

**Need help with translations?** Join our Discord: [http://discord.meteofivem.net/](http://discord.meteofivem.net/)

***

### You're All Set!

**Restart your server** and the Meteo Phone should be working!

***

**Need Help?**

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
