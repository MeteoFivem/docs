---
description: >-
  Meteo pawnshop - sell stolen items for cash and take buyer orders on the
  laptop script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-pawnshop/
---

# Meteo Pawnshop

This is a guide about testing the Meteo V2 pawnshop script designed exclusively for the Meteo V2 package. This is where you sell crime items you found through crimes, either over the counter or through buyer orders on the laptop for better money.

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

***

## Testing Pawnshop

{% stepper %}
{% step %}
Go to pawnshop location: `/tp 67.1083, -1589.0524, 29.5894`
{% endstep %}

{% step %}
So if you have done pickpocket, vehicle searches or house robberies you can sell items like rolex and get money
{% endstep %}

{% step %}
Point target to the pawnbroker NPC and talk to him
{% endstep %}

{% step %}
Pick "I got some stuff" to open your pawnshop storage and put your stolen items in there
{% endstep %}

{% step %}
Then pick "Cash me out" to sell everything in storage for cash at the counter price
{% endstep %}
{% endstepper %}

> Pawnshop is only open from 6 AM to 10 PM

### Laptop Orders

{% stepper %}
{% step %}
Point target at the laptop next to the pawnbroker and use it
{% endstep %}

{% step %}
The Orders page shows buyers who want certain items and pay more than the counter. Take an order
{% endstep %}

{% step %}
Put the exact items from the order in your pawnshop storage with the broker
{% endstep %}

{% step %}
Go back to the laptop and close the order in My job to get paid in cash. The broker will also warn you if you try to cash out items that are meant for your order
{% endstep %}

{% step %}
Orders come in easy, medium and hard tiers. Close more orders to build your reputation and unlock the bigger buyers. The Ledger page shows everything you made through the shop
{% endstep %}
{% endstepper %}

### Item Prices

* rolex: $300-500
* diamond\_ring: $150-250
* tenkgoldchain: $100-180
* goldchain: $60-120
* goldbar: $1000-1500
* laptop: $80-150
* radioscanner: $60-130
* fitbit: $40-90
* tablet: $25-60
* House robbery finds like `meteo_hr_ruby`, `meteo_hr_pocketwatch`, `meteo_hr_locket`, `meteo_hr_tv` and more
* Graveyard dig finds like `meteo_gd_relic`, `meteo_gd_crucifix`, `meteo_gd_signet`, `meteo_gd_goldtooth` and more

### Getting Items to Sell

* Do pickpocket on NPCs. check out [meteo-pickpocket](../meteo-pickpocket/) testing guide
* Search vehicles with screwdriverset. check out [meteo-searchvehicles](../meteo-searchvehicles/) testing guide
* Rob mailboxes. check out [meteo-mailboxrob](../meteo-mailboxrob/) testing guide
* Search dumpsters. check out [meteo-dumpstersearch](../meteo-dumpstersearch/) testing guide
* Rob houses. check out [meteo-houserobbery](../meteo-houserobbery/) testing guide
* Dig graves. check out [meteo-graveyarddig](../meteo-graveyarddig/) testing guide

### Perks

* This is connected to [meteo-perks](../meteo-perks/). Level up the Pawn line to unlock Smooth Talker (better sell prices), Connections (shorter cooldowns), After Hours (pawn 24/7) and Kingpin (more street income)

***

## Good to Know

{% hint style="success" %}
Opening hours, item prices, perk XP and laptop orders are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or move pawnshops (ped and laptop) in-game with the Pawnshops creator on the same page. Storage size and cooldowns stay on our config.
{% endhint %}

{% content-ref url="../meteo-perks/" %}
[meteo-perks](../meteo-perks/)
{% endcontent-ref %}
