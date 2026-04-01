---
description: >-
  Meteo fishing - relaxing passive fishing job, go to fishing spots, catch fish, sell them for profit.
---

# Meteo Fishing Job

Relaxing passive fishing job. Go to fishing spots, cast your line, catch fish, and sell them for profit. No groups, no timers, just chill fishing.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-fishingjob-preview.png" alt=""><figcaption></figcaption></figure>

## Before You Start

- Access to the meteo test server
- Know how to [spawn items](../../how-to-spawn-items.md)
- Familiar with [getting started](../../getting-started.md) basics

***

## Testing Fishing Job

{% stepper %}
{% step %}
**Get the tablet**

Use `/giveitem id meteo_jobtablet` to spawn the tablet. Open tablet and go to fishing job section. This job doesn't require clocking in (clockIn=false), so u can fish anytime from any location.
{% endstep %}

{% step %}
**Get fishing equipment**

Go to fish market at del perro pier (or use `/tp -1833.6630, -1263.6201, 8.6183, 140.6725`). Talk to the npc fisherman. Buy a fishing rod: `meteo_fishing_rod` for $500. Keep the rod in your inventory (it has durability).
{% endstep %}

{% step %}
**Buy bait**

While at fish market, also buy bait from the npc. Three bait types available, each affects what u catch:
- Basic bait: $50 for 10 = best for common fish
- Premium bait: $100 for 10 = good mix of uncommon fish
- Legendary bait: $150 for 5 = best for rare and legendary fish
{% endstep %}

{% step %}
**Find fishing spots**

Open tablet and select fishing job. Click "show fishing spots" button. Blips appear on map for 30 seconds showing all fishing zones. Fishing zones scattered across map: del perro pier, alamo sea, rivers, lakes, beaches. Go to any zone and stand near the water.
{% endstep %}

{% step %}
**Cast your line**

At a fishing spot, equip your fishing rod and bait. Use the rod (action button). Your character casts line into water. U will see "waiting for fish..." status. Fish will bite after random wait (5-15 seconds).
{% endstep %}

{% step %}
**Catch the fish**

When fish bites, u get notification. Skillcheck appears (depends on fish rarity). Common fish: easy skillchecks. Uncommon fish: easy or medium skillchecks. Rare fish: medium skillchecks. Legendary fish: medium or hard skillchecks. Pass the skillcheck to catch the fish. Fail and the fish escapes (lose the bait attempt).
{% endstep %}

{% step %}
**Sell your catch**

Once u have caught fish, take them to any general store npc. Talk to fish buyer and sell entire stack. Instant cash payment based on rarity. All money goes directly to your wallet.
{% endstep %}

{% step %}
**Test different baits**

Go to fish market and buy basic bait. Fish for 10 minutes and note rarity distribution. Go back and buy premium bait. Fish for 10 minutes and note difference. Finally buy legendary bait and fish. U should see increased rarity with better baits. Compare earnings to bait cost for profit analysis.
{% endstep %}

{% step %}
**Test levels**

Start at level 1 and catch some rare fish. Note sell price (e.g. $450). Use `/setcivlevel fishing 5` (testing command) to jump to level 5. Catch same rarity fish and note sell price (should be +20% = $540). Bonus applies immediately when u level up.
{% endstep %}
{% endstepper %}

***

## Good to Know

{% hint style="success" %}
All fishing zones, bait types, fish rarities, sell prices, level bonuses, and achievements are configurable on our config. U can change them once you get the server. We will guide you :)
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-jobtablet/" %}
[meteo-jobtablet](../meteo-jobtablet/) - for job tablet integration
{% endcontent-ref %}

