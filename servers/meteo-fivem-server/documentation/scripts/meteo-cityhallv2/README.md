---
description: >-
  Meteo city hall - 7 civilian jobs and documents script designed exclusively
  for the meteo fivem server.
---

# Meteo City Hall

This is a guide about testing the meteo fivem city hall script designed exclusively for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing City Hall

### Location

* `/tp -1291.8804, -572.3116, 30.5727` and point target and open the city hall

### Job Listings

* City hall has 7 civilian jobs you can apply for:
  * **Taxi** - `/tp 898.02, -175.08` (commission + tips)
  * **Bus** - `/tp 449.60, -650.58` (per route pay)
  * **Delivery** - `/tp 78.30, 112.35` (per package)
  * **Cleaning** - `/tp -105.71, -69.03` (per spot)
  * **Electrician** - `/tp 468.18, -1901.32` (per repair)
  * **Fishing** - `/tp -1833.66, -1263.62` (per fish sold)
  * **Repo Agent** - `/tp 498.47, -1340.03` (per vehicle)
* Browse the jobs and apply for one. Then go to the job location and start working

### Documents

* You can also purchase documents from city hall:
  * ID Card ($150), Driver's License ($350), Weapons License ($750)
  * Police Badge, Lawyer Pass, Judge Badge ($100 each - job restricted)
* There is a 24 hour cooldown after buying a document before you can buy the same one again

### Give Document Command

* Admins and job bosses can give documents to players using `/givedocument`
* Usage: `/givedocument [playerID] [documentType]`

**Document types:**

| Type | Item Given | Who Can Give |
|------|-----------|-------------|
| `idCard` | City ID Card | Admin |
| `driversLicense` | Driver's License | Admin |
| `weaponsLicense` | Weapons License | Admin |
| `policeBadge` | Police Badge | Admin or Police Boss |
| `lawyerPass` | Lawyer Pass | Admin or Lawyer Boss |
| `judgePass` | Judge Badge | Admin or Judge Boss |

**Examples:**

```
/givedocument 1 idCard
/givedocument 1 driversLicense
/givedocument 1 weaponsLicense
/givedocument 1 policeBadge
/givedocument 1 lawyerPass
/givedocument 1 judgePass
```

**Rules:**
* Admins can give any document to any player
* Job bosses can only give documents that match their own job (e.g. police boss can only give policeBadge)
* Boss access is controlled by `Config.bossCanGiveDocuments` (on by default)
* If the player already has that document, it will not give another one
* The document gets the target player's info (name, birthdate, etc.) automatically

> Check out the exclusive video for all details

***

## Good to Know

{% hint style="success" %}
All job locations, document prices and job pay rates are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

{% content-ref url="../meteo-dailyrewards/" %}
[meteo-dailyrewards](../meteo-dailyrewards/)
{% endcontent-ref %}
