---
description: >-
  Send your meteo server logs to Fivemanage so you can view and search every
  action from one dashboard.
icon: file-lines
---

# How to Use Fivemanage for Server Logs

This guide walks you through sending your meteo server logs to Fivemanage. Once set up, every logged action on your server shows up in the Fivemanage logs dashboard, where you can filter and search them by things like a player's citizen ID.

***

{% hint style="warning" %}
**Why not Discord logs?** Discord webhooks are not reliable for logging and have strict rate limits. Once you have a larger amount of players, the webhooks get rate limited and a lot of your actions simply never get logged. Fivemanage has no such limit, so every action is logged no matter how many players are online.
{% endhint %}

***

## What You Need

* A Fivemanage account (free to create)
* About 5 minutes

***

## Steps

{% stepper %}
{% step %}
**Create a Fivemanage account**

Go to <a href="https://fivemanage.com" target="_blank">fivemanage.com</a>. If you do not have an account yet, create a new one.
{% endstep %}

{% step %}
**Create a logs API token**

In your Fivemanage account, go to **API keys** and create a new token with **logs only** access. Copy the API key.
{% endstep %}

{% step %}
**Add the key to ox.cfg**

Open `ox.cfg`, find `fivemanage:key`, and paste your copied API key there. Save the file.
{% endstep %}

{% step %}
**Set the logger to oxlib**

Open `meteo.cfg` and set `meteo:logger` to `"oxlib"`:

```cfg
setr meteo:logger "oxlib"
```

Save the file.
{% endstep %}

{% step %}
**Restart the server**

Restart your server so the new logger settings take effect.
{% endstep %}

{% step %}
**View your logs**

Open the Fivemanage logs dashboard. Logs only show up once actions actually happen on your server, so restarting alone is not enough. Do a few things in game :)

{% hint style="info" %}
If the dashboard feels complex, enable **simple mode**. You can then get a player's citizen ID and paste it into the Fivemanage logs search bar to find every log tied to that player.
{% endhint %}
{% endstep %}
{% endstepper %}

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
