---
description: >-
  Meteo fingerprint scanner - fingerprint scanning and matching script designed
  exclusively for the meteo fivem server.
---

# Meteo Fingerscanner

This is a guide about testing the meteo fivem fingerprint scanner script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Police job: `/setjob yourid police 4`

***

## Testing Fingerprint Scanner

{% stepper %}
{% step %}
Go to the scanner at LSPD: `/tp -577.7416, -116.7539, 33.6111`
{% endstep %}

{% step %}
Point target and click on Scan Fingerprint
{% endstep %}

{% step %}
Must have a nearby player to do this. then it will scan and take the fingerprint id of the player
{% endstep %}

{% step %}
The scanner shows player info - name, date of birth, gender, nationality and their unique fingerprint ID
{% endstep %}

{% step %}
You can copy the fingerprint ID to clipboard for use in reports
{% endstep %}
{% endstepper %}

### Evidence Matching

* Also this is connected with [meteo-evidence](../meteo-evidence/) script
* If any fingerprint matching to that player's fingerprint is found in the evidence database then it will show that on the UI
* It shows up to 5 most recent evidence matches with vehicle plate and which officer extracted it

{% hint style="warning" %}
Make sure to check out [meteo-evidence](../meteo-evidence/) testing guide to learn more about fingerprints and evidence collection
{% endhint %}

***

## Good to Know

{% hint style="success" %}
Scanner location is configurable on our config. you can change it once you get the server. we will guide you :)
{% endhint %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

> Connected with meteo-evidence for fingerprint matching and meteo-policejob for job access
