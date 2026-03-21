---
description: >-
  Meteo fingerprint scanner - fingerprint scanning and matching script
  designed exclusively for the meteo fivem server.
---

# Meteo Fingerprint Scanner

This is a guide about testing the meteo fivem fingerprint scanner script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Police job: `/setjob yourid police 4`

***

## Testing Fingerprint Scanner

* go to the scanner at LSPD: `/tp -577.7416, -116.7539, 33.6111`
* point target and click on Scan Fingerprint
* must have a nearby player to do this. then it will scan and take the fingerprint id of the player
* the scanner shows player info - name, date of birth, gender, nationality and their unique fingerprint ID
* you can copy the fingerprint ID to clipboard for use in reports

### Evidence Matching

* also this is connected with [meteo-evidence](../meteo-evidence/) script
* if any fingerprint matching to that player's fingerprint is found in the evidence database then it will show that on the UI
* it shows up to 5 most recent evidence matches with vehicle plate and which officer extracted it
* make sure to check out [meteo-evidence](../meteo-evidence/) testing guide to learn more about fingerprints and evidence collection

***

## Good to Know

* scanner location is configurable on our config. you can change it once you get the server. we will guide you :)
* connected with [meteo-evidence](../meteo-evidence/) for fingerprint matching and [meteo-policejob](../meteo-policejob/) for job access
