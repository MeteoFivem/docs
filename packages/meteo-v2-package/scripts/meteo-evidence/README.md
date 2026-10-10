---
description: >-
  Meteo evidence - bullet casings, blood, fingerprints, GSR test, drug test, DNA
  swab, breathalyzer, CSI kit and evidence lockers designed exclusively for the
  Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-evidence/
---

# Meteo Evidence

This is a guide about testing the Meteo V2 evidence script designed exclusively for the Meteo V2 package. this is also connected with all of our other scripts like crime system. when criminals are not using gloves etc then it adds fingermarks and police can collect those as evidence and catch them :)

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
* You have to be on duty as a supported job (police by default, changeable in the admin menu under Script Settings > Evidence)

***

## Investigation Mode (CSI Kit)

Evidence on the ground is only visible to an on duty officer in investigation mode.

{% stepper %}
{% step %}
**Turn it on**

get the CSI kit `/giveitem yourid meteo_csi_kit 1` and use it. investigation mode turns on and evidence near you shows up as markers with a small info panel
{% endstep %}

{% step %}
**Collect with a flashlight**

equip `weapon_flashlight`, aim at a marker and press **E** to bag it
{% endstep %}

{% step %}
**Turn it off**

use the kit again to leave investigation mode. turning it on is free and each time you turn it off uses one of the kit's 10 uses. getting downed, dying or being cuffed also drops you out of the mode
{% endstep %}
{% endstepper %}

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

turn on investigation mode with the CSI kit and get `/giveitem yourid weapon_flashlight 1` (police can get this from armory too). you can see bullet casings on the ground
{% endstep %}

{% step %}
**Collect evidence**

you need `empty_evidence_bag` item to collect them - `/giveitem yourid empty_evidence_bag 5`. aim the flashlight at a casing and press **E** to collect it into the evidence bag. the collected evidence will have weapon serial info so police can check and find which weapon was used
{% endstep %}
{% endstepper %}

### Blood Samples

* when players bleed it leaves blood drops on the ground. a bleeding player leaves a trail as they move and a death leaves a splatter or a pool depending on how they died
* blood is drawn as decals on the ground now, not props, so it looks like real blood and costs almost nothing
* use investigation mode and the flashlight to find them and collect with evidence bags same way
* you can also use `bleach` to clean blood drops - `/giveitem yourid bleach 1` (cleans all blood within 5 meters)
* rain washes blood away, so nothing is left on the ground while it rains

{% hint style="warning" %}
**Blood goes off.** DNA degrades with age, so a fresh drop nearly always gives a usable profile and an old one often gives nothing but "Unknown". It starts degrading after 3 minutes and is at its worst by 25 minutes. Get to a scene fast or the blood is worthless.
{% endhint %}

### Vehicle Fingerprints

{% stepper %}
{% step %}
**Leave fingerprints**

when a player enters a vehicle without gloves it leaves a print on the vehicle
{% endstep %}

{% step %}
**Scan with UV light**

use `uv_light` to scan vehicles for fingerprints - `/giveitem yourid uv_light 1`. go near a vehicle (within 3 meters) and use the UV light
{% endstep %}

{% step %}
**One pass does it**

the scan bags any print it finds straight away, so there is no separate collect step. the UV light spends durability as it goes and has 10 uses before quality runs out
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Prints roll a quality when they are created - full, partial or smudged - and that decides how much of the print id survives collection. A smudged print may not match anyone.
{% endhint %}

### GSR Test (Gunshot Residue)

* after a player fires 5+ shots they get gunpowder residue on their hands. it wears off on its own after an hour
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
* DNA and blood sample bags are analysed at the lab bench in the [MDT](../meteo-mdt/) system, where results get matched against the records

### Breathalyzer

* you need a friend to test this since you cant use it on yourself
* have your friend spawn and use some alcohol like `/giveitem theirid whiskey 3` or `/giveitem theirid beer 5`
* then use `breathalyzer` on them - `/giveitem yourid breathalyzer 1`
* it measures BAC (blood alcohol content)
* legal limit is 0.08%
* result can be stored as evidence

***

## Evidence Storage

{% hint style="info" %}
The old analyze station is gone from this script. Fingerprint and DNA analysis is done at the lab bench and evidence intake that are part of [meteo-mdt](../meteo-mdt/) - check its guide for that.
{% endhint %}

### Evidence Locker (Storage)

{% stepper %}
{% step %}
**Go to evidence storage**

LSPD: `/tp -543.9750, -111.7047, 43.8567` or Blane County: `/tp 1036.8206, 2723.0754, 38.6572`. these are the two stations the package ships with
{% endstep %}

{% step %}
**Create and manage lockers**

you can create new evidence lockers with custom names (like Case-2024-001). each locker has 50 slots. you can search and browse all evidence lockers. every station opens the same lockers
{% endstep %}
{% endstepper %}

### Evidence Station Creator

* Open the admin menu with `/admin` and go to Script Settings > Evidence
* In the Creator section you can add, move or remove police stations where officers open the evidence lockers - give it a name and aim at the locker spot
* In the same menu you can pick which jobs can use evidence

{% hint style="info" %}
this is also connected with [meteo-mdt](../meteo-mdt/). you can link evidence lockers to reports on MDT, and every locker action is pushed to the MDT activity log so it shows on the officer's roster profile
{% endhint %}

***

## Good to Know

{% hint style="success" %}
The jobs that can use evidence are editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit the police stations where officers open the evidence lockers in-game with the Evidence creator. Script Settings is god-tier only.
{% endhint %}

* criminals wearing gloves dont leave fingerprints or evidence - thats the whole point of the script
* entering a vehicle no longer drops a print on the floor. the print stays on the vehicle itself, so a UV scan is the only way to pull it
* blood DNA degrades with age and rain washes blood away, so response time matters
* evidence left on the ground clears itself after 30 minutes

**Connected scripts:**

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

> Lifting a suspect's fingerprints in the field and running lab orders are handled through the MDT now - see the [meteo-mdt](../meteo-mdt/) guide for the lab bench and evidence intake
