---
description: >-
  Meteo fishing job - cast anywhere you face open water, reel tension minigame,
  rod condition, bait that goes off over time, 4 fish rarity tiers and level
  based sell bonuses designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-fishingjob/
---

# Meteo Fishing Job

This is a guide about testing the Meteo V2 fishing job script designed exclusively for the Meteo V2 package. Fish anywhere you face open water - no fishing zones. A reel tension minigame to land your catch, a rod bait box, rod condition and bait freshness that change your bite time and catch rarity, 3 bait types, 4 fish rarity tiers with weight-based prices, 5 levels with sell price bonuses and achievements tracked in the phone Labor app.

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
* Have your [phone](../meteo-phone/) ready to see your fishing level, awards and history in the Labor app

***

## Testing Fishing Job

{% stepper %}
{% step %}
**No clock in needed**

fishing is not a dispatch job - there is no clocking in. open the Labor app on your phone and you will see fishing listed with your level and progress. just get your gear and go fish anytime
{% endstep %}

{% step %}
**Get fishing equipment**

go to the fish market at del perro pier (or use `/tp -1833.6630, -1263.6201, 8.6183, 140.6725`). talk to the fish market vendor and pick "buy supplies". buy a fishing rod: `meteo_fishing_rod` for $500
{% endstep %}

{% step %}
**Buy bait**

from the same shop, buy bait. three bait types are available, each changes what you catch:

* `meteo_bait_basic`: $50 for 10 - mostly common fish
* `meteo_bait_premium`: $100 for 10 - better mix of uncommon and rare fish
* `meteo_bait_legendary`: $150 for 5 - best chance at rare and legendary fish
{% endstep %}

{% step %}
**Load the bait box**

bait goes inside your rod, not your pockets. open your inventory, use the "Open Bait Box" button on the fishing rod and drag your bait into it. the box has 5 slots and only accepts bait. each rod has its own box
{% endstep %}

{% step %}
**Cast your line**

walk up to any open water (pier, beach, lake, river) and face it. use the fishing rod. the script detects water in front of you automatically - if there is no water or a wall is in the way, you will get "You need to face open water to fish". once cast, your character keeps fishing and recasts automatically until you run out of bait. press RMB, use the rod again, move away, enter a vehicle or start swimming to stop
{% endstep %}

{% step %}
**Reel in the fish**

when you get "Something is biting!" the reel minigame opens. hold LMB to increase tension and release to ease off. keep the tension inside the zone to fill the catch bar. the fish pulls in bursts, so watch out:

* tension maxed out too long - the line snaps
* tension at zero too long or the time runs out - the fish gets away

rarer fish are harder: common = easy, uncommon = medium, rare = hard, legendary = extreme. one bait is used on every bite, caught or not
{% endstep %}

{% step %}
**Sell your catch**

go back to a fish market, talk to the vendor and pick "sell all fish". you get cash for every fish in your inventory with a sale breakdown. your level bonus and perk bonus are added on top
{% endstep %}
{% endstepper %}

***

## Fish Rarity And Value

every fish has its own weight. a heavier fish sells closer to the top of its price range.

**Common fish**: bass, bluegill, catfish, carp, trout

* sell for $50-80 each
* xp: 5-10 per fish
* easy minigame

**Uncommon fish**: salmon, pike, walleye, perch

* sell for $120-200 each
* xp: 12-20 per fish
* medium minigame

**Rare fish**: sturgeon, muskie, steelhead

* sell for $350-500 each
* xp: 25-40 per fish
* hard minigame

**Legendary fish**: blue marlin, bluefin tuna

* sell for $750-1200 each
* xp: 50-80 per fish
* extreme minigame

***

## Rod Condition

your rod loses 2 condition every time you land a fish and breaks at 0 (\~50 catches). any bait still inside a broken rod is returned to your pockets. rod condition also changes how you fish:

* 75% and above: shorter wait for a bite, better chance at rarer fish and an easier minigame
* 40-74%: normal
* below 40%: longer wait for a bite

***

## Bait Freshness

bait goes off over time (2 days real time by default). you can see its freshness bar on the item. stale bait still works but is worse:

* fresh bait: normal wait and normal catch chances
* going off: longer wait and lower chance at rare fish
* nearly gone: even longer wait and lower rarity again
* spoiled bait is skipped - if only spoiled bait is left in the box you will get "Your bait has gone bad"

***

## Levels And Perks

* level 1 (novice angler): base earnings
* level 2 (amateur fisher): +5% sell price, small rarity boost (200 xp)
* level 3 (skilled angler): +10% sell price, bigger rarity boost (600 xp)
* level 4 (expert fisher): +15% sell price, bigger rarity boost (1500 xp)
* level 5 (master angler): +20% sell price, best rarity boost (3500 xp)
* level up by catching fish. every catch also gives civilian perk xp, and every sale gives Labor reputation

***

## Achievements

check your progress and collect rewards in the Awards tab of the Labor app on your phone.

* first catch - catch your first fish
* hobby fisher - catch 50 fish
* seasoned angler - catch 250 fish
* fish whisperer - catch 500 fish
* legendary angler - catch 1000 fish
* rare find - catch your first rare fish
* once in a lifetime - catch your first legendary fish
* big earner - earn $10,000 from fishing
* master angler - reach the highest fishing level

***

## Testing Bait Types

load basic bait and fish for a while, note the rarity of your catches. then try premium bait and finally legendary bait. you should see more rare and legendary fish with better baits. compare your earnings to the bait cost

***

## Testing Rod And Bait Quality

fish with a fresh rod and fresh bait and note how long bites take. keep fishing until the rod drops below 40% and compare - bites take longer and the minigame no longer gets the easy step. stale bait does the same to your bite time and rarity

***

## Good to Know

{% hint style="success" %}
fishing is a non-dispatch, solo job - no clocking in and no groups. there are no fishing zones, you can fish from any spot where you face open water. bait is only used from the rod bait box. a fish market sells the rod and bait and buys your catch, and you have to be close to it to buy or sell. levels, awards and your sale history show up in the Labor app on your phone.

Rod price and wear, bait prices, packs and rarity chances, fish prices, xp and which fish there are, bite wait, how fast bait goes off, perk xp, reputation and achievement rewards are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit fish markets in-game with the Fishing Job creator - place the vendor, pick the ped, idle animation, counter reach and map marker.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

{% content-ref url="../meteo-manage/" %}
[meteo-manage](../meteo-manage/)
{% endcontent-ref %}
