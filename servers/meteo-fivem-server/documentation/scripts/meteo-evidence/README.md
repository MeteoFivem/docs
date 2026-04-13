---
description: >-
  Meteo evidence - bullet casings, blood, fingerprints, GSR test, drug test, DNA
  swab, breathalyzer, evidence analysis and storage designed exclusively for the
  meteo fivem server.
---

# Meteo Evidence

This is a guide about testing the meteo fivem evidence script designed exclusively for meteo server. this is also connected with all of our other scripts like crime system. when criminals are not using gloves etc then it adds fingermarks and police can collect those as evidence and catch them :)

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Police job: `/setjob yourid police 4`
* Police players can get evidence items from the police job armory. check out [meteo-policejob](../meteo-policejob/) testing guide for that

***

## Testing Evidence Collection

### Bullet Casings

{% stepper %}
{% step %}
**Shoot a weapon**

get any weapon `/giveitem yourid weapon_pistol 1` and shoot a few times
{% endstep %}

{% step %}
**Use flashlight**

get `/giveitem yourid weapon_flashlight 1` (police can get this from armory too). aim flashlight and you can see bullet casings on the ground
{% endstep %}

{% step %}
**Collect evidence**

you need `empty_evidence_bag` item to collect them - `/giveitem yourid empty_evidence_bag 5`. go near a casing and press **E** to collect it into the evidence bag. the collected evidence will have weapon serial info so police can check and find which weapon was used
{% endstep %}
{% endstepper %}

### Blood Samples

* when players bleed it leaves blood drops on the ground
* use flashlight to find them and collect with evidence bags same way
* you can also use `bleach` to clean blood drops - `/giveitem yourid bleach 1` (cleans all blood within 5 meters)

### Vehicle Fingerprints

{% stepper %}
{% step %}
**Leave fingerprints**

when a player enters a vehicle without gloves it leaves fingerprints
{% endstep %}

{% step %}
**Scan with UV light**

use `uv_light` to scan vehicles for fingerprints - `/giveitem yourid uv_light 1`. go near a vehicle (within 3 meters) and use the UV light to scan. UV light has 10 uses before quality runs out
{% endstep %}

{% step %}
**Collect evidence**

collect the fingerprint evidence with evidence bags
{% endstep %}
{% endstepper %}

### GSR Test (Gunshot Residue)

* after a player fires 5+ shots they get gunpowder residue on their hands (70% chance)
* use `residue_swab` on a suspect to test for GSR - `/giveitem yourid residue_swab 1`
* it will show positive or negative result
* suspects can wash GSR off in water (takes 15 seconds) or use `hand_wipes`

### Drug Test

* you need a friend to test this since you cant use it on yourself
* have your friend spawn and use some drugs like `/giveitem theirid meth 1` or `/giveitem theirid cokebaggy 1` or `/giveitem theirid joint 1`
* then use `drug_test_kit` on them - `/giveitem yourid drug_test_kit 1`
* it detects stimulants (cocaine), methamphetamine (meth) and cannabis (weed)
* test result can be stored as evidence

### DNA Swab

* you need a friend to test this since you cant use it on yourself
* use `dna_swab` on a suspect to collect their DNA - `/giveitem yourid dna_swab 1`
* stand near the suspect (within 2 meters) and use the item
* it collects the suspect's DNA as an evidence bag with DNA ID, blood type and suspect name
* then go to the analyze station and analyze the DNA evidence bag to extract the DNA profile
* the extracted DNA profile gets saved to the database so you can search and compare later
* you can also extract DNA from blood sample evidence bags the same way

### Breathalyzer

* you need a friend to test this since you cant use it on yourself
* have your friend spawn and use some alcohol like `/giveitem theirid whiskey 3` or `/giveitem theirid beer 5`
* then use `breathalyzer` on them - `/giveitem yourid breathalyzer 1`
* it measures BAC (blood alcohol content)
* legal limit is 0.08%
* result can be stored as evidence

***

## Evidence Analyze And Storage

### Analyze Evidence

{% stepper %}
{% step %}
**Go to analyze location**

LSPD: `/tp -543.8995, -117.1329, 43.8566` or Blane County: `/tp 1037.6584, 2725.7361, 38.6571`
{% endstep %}

{% step %}
**Analyze fingerprints and DNA**

here you can view analyzed fingerprints, search by ID or plate, and extract fingerprints from collected vehicle evidence. you can also view and search analyzed DNA profiles, and extract DNA from blood sample or DNA swab evidence bags
{% endstep %}
{% endstepper %}

### Evidence Locker (Storage)

{% stepper %}
{% step %}
**Go to evidence storage**

LSPD: `/tp -543.9750, -111.7047, 43.8567` or Blane County: `/tp 1036.8206, 2723.0754, 38.6572`
{% endstep %}

{% step %}
**Create and manage lockers**

you can create new evidence lockers with custom names (like Case-2024-001). each locker has 50 slots. you can search and browse all evidence lockers
{% endstep %}
{% endstepper %}

{% hint style="info" %}
this is also connected with [meteo-mdt](../meteo-mdt/). you can link evidence lockers to reports on MDT
{% endhint %}

***

## Good to Know

{% hint style="success" %}
all evidence settings like GSR shots required, GSR chance, UV light uses, drug test types, BAC legal limit, DNA analysis and locker sizes are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* criminals wearing gloves dont leave fingerprints or evidence - thats the whole point of the script

**Connected scripts:**

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-fingerscanner/" %}
[meteo-fingerscanner](../meteo-fingerscanner/)
{% endcontent-ref %}
