---
description: >-
  Disable the default chat messages and console prints that appear on server
  start.
icon: comment-slash
---

# How to Remove Acknowledge Messages

By default, the meteo server prints a few welcome/info messages in chat and the console (links to our Discord, docs, and a thank-you message). If you do not want these to show on your server, you can turn them off with one config line.

***

## Steps

{% stepper %}
{% step %}
**Open `meteo.cfg`**

Find the `meteo.cfg` file in your server config folder and open it.
{% endstep %}

{% step %}
**Find the acknowledge line**

Look for this line:

```
setr meteo:acknowledge true
```
{% endstep %}

{% step %}
**Change it to `false`**

```
setr meteo:acknowledge false
```
{% endstep %}

{% step %}
**Restart the server**

The default chat messages and console prints will no longer appear.
{% endstep %}
{% endstepper %}

***

## What gets disabled

The chat messages shown below (and matching console prints) will no longer be sent on server start:

<figure><img src="../../../../.gitbook/assets/meteo_acknowledge.png" alt=""><figcaption><p>Default acknowledge messages shown in chat</p></figcaption></figure>

The on-screen copyright text is removed as well:

<figure><img src="../../../../.gitbook/assets/meteo_acknowledge_watermark.png" alt=""><figcaption><p>Copyright text shown on screen</p></figcaption></figure>

***