---
description: >-
  Meteo fishing job - relaxing passive fishing job designed exclusively for the
  meteo fivem server.
---

# Meteo Fishing Job

This is a guide about testing the meteo fivem fishing job script designed exclusively for meteo server. relaxing passive fishing job. go to fishing spots, cast your line, catch fish, and sell them for profit. no groups, no timers, just chill fishing.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-fishingjob-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to/how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics
* Have the [job tablet](../meteo-jobtablet/) ready

***

## Testing Fishing Job

{% stepper %}
{% step %}
**Open the tablet**

use `/giveitem id meteo_jobtablet` to spawn the tablet. open tablet and go to fishing job section. this job doesnt require clocking in (clockIn=false). you can fish anytime from any location
{% endstep %}

{% step %}
**Get fishing equipment**

go to fish market at del perro pier (or use `/tp -1833.6630, -1263.6201, 8.6183, 140.6725`). talk to the npc fisherman. buy a fishing rod: `meteo_fishing_rod` for $500. keep the rod in your inventory (it has durability)
{% endstep %}

{% step %}
**Buy bait**

while at fish market, also buy bait from the npc. three bait types available, each affects what you catch:
- basic bait: $50 for 10 = best for common fish (mostly bass, carp, etc)
- premium bait: $100 for 10 = good mix of uncommon fish (salmon, pike, etc)
- legendary bait: $150 for 5 = best for rare and legendary fish (marlin, tuna, etc)

more expensive bait = better rarity chance
{% endstep %}

{% step %}
**Find fishing spots**

open tablet and select fishing job. click "show fishing spots" button. blips appear on map for 30 seconds showing all fishing zones. fishing zones scattered across map: del perro pier, alamo sea, rivers, lakes, beaches. go to any zone and stand near the water
{% endstep %}

{% step %}
**Cast your line**

at a fishing spot, equip your fishing rod and bait. use the rod (action button). your character casts line into water. you will see "waiting for fish..." status. fish will bite after random wait (5-15 seconds)
{% endstep %}

{% step %}
**Catch the fish**

when fish bites, you get notification. skillcheck appears (depends on fish rarity):
- common fish: easy skillchecks (should pass easily)
- uncommon fish: easy or medium skillchecks
- rare fish: medium skillchecks (need to focus)
- legendary fish: medium or hard skillchecks (hardest!)

pass the skillcheck to catch the fish. fail and the fish escapes (lose the bait attempt)
{% endstep %}

{% step %}
**Sell your catch**

once you have caught fish, take them to any general store npc. talk to fish buyer and sell entire stack. instant cash payment based on rarity. all money goes directly to your wallet
{% endstep %}
{% endstepper %}

***

## Fish Rarity And Value

**Common fish**: bass, bluegill, catfish, carp, trout
* sell for $50-80 each
* xp: 5-10 per fish
* easy skillchecks

**Uncommon fish**: salmon, pike, walleye, perch
* sell for $120-200 each
* xp: 12-20 per fish
* easy/medium skillchecks

**Rare fish**: sturgeon, muskie, steelhead
* sell for $350-500 each (big money!)
* xp: 25-40 per fish
* medium skillchecks (tougher!)

**Legendary fish**: blue marlin, bluefin tuna
* sell for $750-1200 each (jackpot!)
* xp: 50-80 per fish
* medium/hard skillchecks (very difficult!)

***

## Rod Durability

fishing rod loses durability with each catch: -2 durability per fish. rod starts at 100 durability. after ~50 catches, rod breaks and you need to buy new one. broken rod = must replace it. fish items are stackable, rods are not

***

## Bait Strategy

* basic bait: cheap but mostly common fish (test early levels)
* premium bait: good balance of uncommon catches (mid-game)
* legendary bait: expensive but best chance at rare/legendary (high earnings)
* you need bait in inventory to fish, bait consumed on each attempt
* legendary bait = best profit ratio when landing rare/legendary fish

***

## Levels And Perks

* level 1 (novice): base earnings
* level 2 (amateur): +5% sell price bonus (200 xp required)
* level 3 (skilled): +10% sell price bonus (600 xp required)
* level 4 (expert): +15% sell price bonus (1500 xp required)
* level 5 (master): +20% sell price bonus + increased rare catch rate (3500 xp required)
* higher levels = better fish prices when you sell
* level up by catching more fish (each gives xp)

***

## Achievements

* catch 10 fish
* catch 50 fish
* catch 100 fish
* catch 5 uncommon fish
* catch 5 rare fish
* catch 5 legendary fish
* earn $10,000 from fishing
* earn $50,000 from fishing
* each achievement tracks progress

***

## Testing Bait Types

go to fish market and buy basic bait. fish for 10 minutes and note rarity distribution. go back and buy premium bait. fish for 10 minutes and note difference. finally buy legendary bait and fish. you should see increased rarity with better baits. compare earnings to bait cost for profit analysis

***

## Testing All Fishing Zones

use "show fishing spots" to see all 14+ fishing zones on map. test different zones: del perro pier, vespucci beach, alamo sea, rivers, lakes, paleto bay. fishing quality/rarity same at all zones (no special zones). zones just for roleplay/location variety. all zones have similar catch chances

***

## Testing Levels And Sell Bonus

start at level 1 and catch some rare fish. note sell price (e.g. $450). use `/setcivlevel fishing 5` (testing command) to jump to level 5. catch same rarity fish and note sell price (should be +20% = $540). bonus applies immediately when you level up

***

## Testing Skillcheck Difficulty

* catch 5 common fish (easy skillchecks - should all succeed)
* catch 5 rare fish (medium skillchecks - some might fail)
* catch 5 legendary fish (hard skillchecks - very challenging!)
* failure rate increases with rarity
* skilled player will catch more legendary fish than casual player

***

## Passive Fishing Strategy

this job is passive income - you dont need to do anything else. while waiting for fish to bite, you can tab out or do other stuff. each cast takes ~5-15 seconds of waiting. legendary bait fishing: high risk/reward (harder skillchecks but best money). basic bait fishing: relaxed, steady income, easier skillchecks

{% hint style="warning" %}
Check out [test-commands](../meteo-jobtablet/test-commands.md) to skip the grind during testing
{% endhint %}

***

## Good to Know

{% hint style="success" %}
fishing is non-dispatch job (no clocking in, just go fish anytime). fishing rod purchased at shop, bait also purchased there. three bait types each bias rarity rolls differently via rarityWeights in config. fish rarities determined by bait type used and random chance. skillcheck difficulty scales with rarity (common=easy, legendary=hard). rod durability depletes at 2 per catch (50 catches per rod). sell prices vary within rarity range (e.g. $350-500 for rare fish). xp rewards per fish also vary within rarity range. levels give sell price bonus: +5% per level (5-20% total). legendary bait highest profit ratio if you catch rare/legendary fish. 14+ fishing spots across map: piers, beaches, ocean, rivers, lakes. once you get the server. we will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet, achievements, rankings
{% endcontent-ref %}
