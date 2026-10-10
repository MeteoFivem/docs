---
description: >-
  Meteo city hall - civilian job finder, businesses, documents and MDT licenses
  script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-cityhallv2/
    - packages/meteo-v2-package/scripts/meteo-cityhallv2/
---

# Meteo City Hall

This is a guide about testing the Meteo V2 city hall script designed exclusively for the Meteo V2 package. City hall is where players see which jobs they can do right now, find businesses and whitelisted departments, and buy their documents and licenses.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing City Hall

{% stepper %}
{% step %}
**Location**

Use `/tp -1291.8804, -572.3116, 30.5727`, point target at the city hall NPC and open the city hall
{% endstep %}

{% step %}
**Overview**

The overview shows your playtime, whether you have a City ID and a driver's license, your cash on hand and the jobs that are open to you right now
{% endstep %}

{% step %}
**Jobs**

Browse the civilian jobs. Each job shows what it needs (City ID, driver's license, playtime) and if you are eligible. Click GPS to mark the job location on your map:

* **Taxi Driver** - `/tp 898.02, -175.08, 73.82`
* **Bus Driver** - `/tp 449.60, -650.58, 28.48`
* **Delivery Driver** - `/tp 78.30, 112.35, 81.17`
* **Cleaner** - `/tp -105.71, -69.03, 58.86`
* **Electrician** - `/tp 468.18, -1901.32, 25.37`
* **Fisher** - `/tp -1833.66, -1263.62, 8.62`
* **Repo Agent** - `/tp 498.47, -1340.03, 29.31`

Then go to the job location. Civilian jobs are clocked in and out from the Labor app on [meteo-phone](../meteo-phone/)
{% endstep %}

{% step %}
**Businesses and Whitelisted Jobs**

The Businesses tab lists the restaurants, shops and clubs in the city with a GPS button. The Whitelist jobs tab lists departments like police, EMS, real estate, mechanic, lawyer and judge. These run their own recruitment, so mark one on your GPS and go introduce yourself
{% endstep %}

{% step %}
**Documents**

You can buy documents with cash:

* **City ID Card** ($150)
* **Police Badge**, **Lawyer Pass**, **Judge Badge** ($100 each - only shown to that job)

There is a 24 hour cooldown after buying a document before you can buy the same one again
{% endstep %}

{% step %}
**Licenses From the MDT**

Licenses like the driver's license come from the [meteo-mdt](../meteo-mdt/) now. Any license type marked as obtainable in the MDT shows up in city hall on its own, with its name and price from the MDT. If you hold a license but lost the card, you can reprint it for a small fee
{% endstep %}
{% endstepper %}

### Give Document Command

* Admins and job bosses can give documents to players using `/givedocument`
* Usage: `/givedocument [playerID] [document]`

**Document types:**

| Type | Item Given | Who Can Give |
|------|-----------|-------------|
| `idCard` | City ID Card | Admin |
| `policeBadge` | Police Badge | Admin or Police Boss |
| `lawyerPass` | Lawyer Pass | Admin or Lawyer Boss |
| `judgePass` | Judge Badge | Admin or Judge Boss |
| License serial from the MDT | That license card | Admin |

**Examples:**

```
/givedocument 1 idCard
/givedocument 1 policeBadge
/givedocument 1 lawyerPass
/givedocument 1 judgePass
```

**Rules:**
* Admins can give any document or MDT license to any player, for free
* Job bosses can only give documents that match their own job (e.g. police boss can only give policeBadge)
* Boss access is controlled by `Config.bossCanGiveDocuments` (on by default)
* If the player already has that document, it will not give another one
* The document gets the target player's info (name, birthdate, etc.) automatically
* Who counts as a city hall admin can be set in the admin menu (Staff > Roles)

> Check out the exclusive video for all details

***

## Good to Know

{% hint style="success" %}
City hall locations, jobs and their requirements, businesses, whitelisted jobs and document prices are configurable on our config. License names and prices are set in the MDT. You can change them once you get the package. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-dailyrewards/" %}
[meteo-dailyrewards](../meteo-dailyrewards/)
{% endcontent-ref %}
