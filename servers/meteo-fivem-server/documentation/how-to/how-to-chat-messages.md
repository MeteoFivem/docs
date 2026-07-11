---
description: >-
  How to change the chat welcome message and rotating auto-messages on your
  meteo fivem server via meteo.cfg.
icon: comments
---

# How to Change Chat Messages

The chat welcome message (shown when a player joins) and the rotating auto-messages are both set in `meteo.cfg`. No script edits needed.

***

## Steps

{% stepper %}
{% step %}
**Open meteo.cfg**

Open your server's `meteo.cfg` file and find the **Meteo Chat** section:

```
setr meteo:chat_welcome "Welcome to the Meteo Server! Press T to open chat and type / to see available commands."
setr meteo:chat_automessages "Don't Forget to join Meteo Discord!|Don't break the rules!|Have fun!"
```
{% endstep %}

{% step %}
**Change the welcome message**

Edit `meteo:chat_welcome` to whatever you want players to see when they join:

```
setr meteo:chat_welcome "Welcome to My Server! Read the rules in our Discord."
```
{% endstep %}

{% step %}
**Change the auto-messages**

`meteo:chat_automessages` is a list of messages that rotate in chat. Separate each message with a pipe `|`:

```
setr meteo:chat_automessages "Join our Discord!|No RDM or VDM|Have fun and roleplay!"
```

Add or remove as many messages as you want - just keep them split by `|`.
{% endstep %}

{% step %}
**Restart your server**

Save `meteo.cfg` and restart your server for the changes to take effect.
{% endstep %}
{% endstepper %}

***

## Settings Reference

| Setting | Description |
| ------- | ----------- |
| `meteo:chat_welcome` | Message shown to a player when they join the server |
| `meteo:chat_automessages` | Rotating auto-messages - separate each one with a pipe `\|` |

***

{% hint style="info" %}
Want to turn off the default join messages entirely instead? See [How to Remove Acknowledge Messages](how-to-remove-acknowledge.md).
{% endhint %}

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
