---
description: >-
  How to set up Cloudflare TURN for video calling on the meteo fivem server.
  Required for phone video calls via WebRTC.
icon: video
---

# How to Set Up Cloudflare TURN

The phone uses Cloudflare TURN for video calling via WebRTC. Without it, players will have issues with video calls. Setup takes 2 minutes.

***

## Steps

{% stepper %}
{% step %}
**Create a Cloudflare account**

Create a Cloudflare account if you dont have one at [cloudflare.com](https://www.cloudflare.com/)
{% endstep %}

{% step %}
**Open the TURN Server page**

Go to [dash.cloudflare.com/?to=/:account/realtime/turn/overview](https://dash.cloudflare.com/?to=/:account/realtime/turn/overview) (or navigate to **Realtime → TURN Server** from the Cloudflare dashboard)
{% endstep %}

{% step %}
**Create the TURN token**

Press **Create**. Give it a name (anything works, like "meteo-phone") and press **Create** again.
{% endstep %}

{% step %}
**Copy your values**

You will now see two values - **Turn Token ID** and **API Token**. Keep this page open, you will paste them in the next step.
{% endstep %}

{% step %}
**Add them to meteo.cfg**

Open `meteo.cfg` and set these two lines:

```
set meteo:phone_cf_turn_token_id "YOUR_TURN_TOKEN_ID"
set meteo:phone_cf_turn_api_token "YOUR_API_TOKEN"
```

Replace the values with the ones you copied from Cloudflare
{% endstep %}

{% step %}
**Restart the server**

Save `meteo.cfg` and restart your server. Video calling should now work in the phone.
{% endstep %}
{% endstepper %}

***

{% hint style="warning" %}
Without this setup, video calls in the phone will not work. Make sure both values are correctly set in `meteo.cfg`.
{% endhint %}

{% hint style="info" %}
For the full list of phone API keys (FiveManage, Gemini, OpenRouter etc.) see the [Configuration Guide](../configuration-guide.md#meteo-phone-api-keys).
{% endhint %}
