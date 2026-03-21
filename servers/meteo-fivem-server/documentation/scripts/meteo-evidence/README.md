---
description: >-
  Meteo evidence - bullet casings, blood, fingerprints, GSR and drug tests
  designed exclusively for the meteo fivem server.
---

# Meteo Evidence

This is a guide about testing the meteo fivem advanced evidence script designed exclusively for meteo server. this is also connected with all of our other scripts like crime system. when criminals are not using gloves etc then it adds fingermarks and police can collect those as evidence and catch them :)

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Police job: `/setjob yourid police 4`

***

## Testing Evidence Collection

### Bullet Casings

{% stepper %}
{% step %}
Get any weapon `/giveitem yourid weapon_pistol 1` and shoot a few times
{% endstep %}

{% step %}
Then get `/giveitem yourid weapon_flashlight 1` (police can get this from armory too)
{% endstep %}

{% step %}
Aim flashlight and you can see bullet casings on the ground
{% endstep %}

{% step %}
You need `empty_evidence_bag` item to collect them - `/giveitem yourid empty_evidence_bag 5`
{% endstep %}

{% step %}
Go near a casing and press **E** to collect it into the evidence bag
{% endstep %}

{% step %}
The collected evidence will have weapon serial info so police can check and find which weapon was used
{% endstep %}
{% endstepper %}

### Blood Samples

* When players bleed it leaves blood drops on the ground
* Use flashlight to find them and collect with evidence bags same way
* You can also use `bleach` to clean blood drops - `/giveitem yourid bleach 1` (cleans all blood within 5 meters)

### Vehicle Fingerprints

{% stepper %}
{% step %}
When a player enters a vehicle without gloves it leaves fingerprints
{% endstep %}

{% step %}
Use `uv_light` to scan vehicles for fingerprints - `/giveitem yourid uv_light 1`
{% endstep %}

{% step %}
Go near a vehicle (within 3 meters) and use the UV light to scan
{% endstep %}

{% step %}
UV light has 10 uses before quality runs out
{% endstep %}

{% step %}
Collect the fingerprint evidence with evidence bags
{% endstep %}
{% endstepper %}

### GSR Test (Gunshot Residue)

* After a player fires 5+ shots they get gunpowder residue on their hands (70% chance)
* Use `residue_swab` on a suspect to test for GSR - `/giveitem yourid residue_swab 1`
* It will show positive or negative result
* Suspects can wash GSR off in water (takes 15 seconds) or use `hand_wipes`

### Drug Test

* You need a friend to test this since you cant use it on yourself
* Have your friend spawn and use some drugs like `/giveitem theirid meth 1` or `/giveitem theirid cokebaggy 1` or `/giveitem theirid joint 1`
* Then use `drug_test_kit` on them - `/giveitem yourid drug_test_kit 1`
* It detects stimulants (cocaine), methamphetamine (meth) and cannabis (weed)
* Test result can be stored as evidence

### Breathalyzer

* You need a friend to test this since you cant use it on yourself
* Have your friend spawn and use some alcohol like `/giveitem theirid whiskey 3` or `/giveitem theirid beer 5`
* Then use `breathalyzer` on them - `/giveitem yourid breathalyzer 1`
* It measures BAC (blood alcohol content)
* Legal limit is 0.08%
* Result can be stored as evidence

***

## Evidence Analyze and Storage

### Analyze Evidence

{% stepper %}
{% step %}
Go to analyze location at LSPD: `/tp -543.8995, -117.1329, 43.8566`
or Blane County: `/tp 1037.6584, 2725.7361, 38.6571`
{% endstep %}

{% step %}
Here you can view analyzed fingerprints, search by ID or plate, and extract fingerprints from collected vehicle evidence
{% endstep %}
{% endstepper %}

### Evidence Locker (Storage)

{% stepper %}
{% step %}
After analyzing go to evidence storage at LSPD: `/tp -543.9750, -111.7047, 43.8567`
or Blane County: `/tp 1036.8206, 2723.0754, 38.6572`
{% endstep %}

{% step %}
You can create new evidence lockers with custom names (like Case-2024-001)
{% endstep %}

{% step %}
Each locker has 50 slots
{% endstep %}

{% step %}
You can search and browse all evidence lockers
{% endstep %}
{% endstepper %}

> Also this is connected with [meteo-mdt](../meteo-mdt/). you can link evidence lockers to reports on MDT

***

## Good to Know

{% hint style="success" %}
All evidence settings like GSR shots required, GSR chance, UV light uses, drug test types, BAC legal limit and locker sizes are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* Criminals wearing gloves dont leave fingerprints or evidence - thats the whole point of the script

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-fingerscanner/" %}
[meteo-fingerscanner](../meteo-fingerscanner/)
{% endcontent-ref %}

> Connected with meteo-policejob, meteo-mdt, meteo-fingerscanner and crime system
