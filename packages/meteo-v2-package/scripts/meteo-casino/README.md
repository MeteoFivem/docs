---
description: >-
  Meteo casino - Diamond Casino with blackjack, roulette, slots, lucky wheel and
  cashier script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-casino/
---

# Meteo Casino

This is a guide about testing the Meteo V2 casino script designed exclusively for the Meteo V2 package.

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

## Testing Casino

The whole Diamond Casino lives in one script: blackjack, roulette, slots, the lucky wheel, the cashier and the PA announcer. Everything plays with the `casinochips` item.

### Getting There

{% stepper %}
{% step %}
`/tp 921.8215, 47.0468, 81.1019` to teleport to the casino
{% endstep %}

{% step %}
Walk inside. The whole floor loads when you enter - dealers, tables, slot reels, the wheel and the cashier. When you walk out it unloads again, so nothing runs while you are across the map
{% endstep %}
{% endstepper %}

### Buying Chips

{% stepper %}
{% step %}
Go to the cashier and pick buy or sell. Chips are $1 each by default, from 10 up to 100,000 chips
{% endstep %}

{% step %}
Use the arrow keys to change the amount, `Enter` to confirm and `Backspace` to leave
{% endstep %}

{% step %}
Anything the casino owes you (a payout that could not fit in your inventory, or a bet refunded after a restart) is handed over when you open the cashier
{% endstep %}
{% endstepper %}

### Lucky Wheel

{% stepper %}
{% step %}
Go to the lucky wheel and spin it. Each spin costs $500 cash and you get 5 spins a day per character. Only one player can use the wheel at a time
{% endstep %}

{% step %}
Rewards are cash, casino chips, tint crates, VIP crates and a 1 in 70 chance at the podium car. Crates are weapon skins - see the [meteo-rewards](../meteo-rewards/) guide
{% endstep %}

{% step %}
If you win the car, it is announced over the casino PA and you get an email on your phone with the plate
{% endstep %}
{% endstepper %}

### Roulette

{% stepper %}
{% step %}
Sit at a roulette table. There are 8 tables in three tiers: Junior (blue) $10 - $500, Standard (green) $500 - $10K and VIP (purple) $10K - $120K. Those limits are per chip
{% endstep %}

{% step %}
Press `R` for the overhead camera, move the chip with the mouse and press `Enter` to place it. A chip between two spots splits the bet
{% endstep %}

{% step %}
You have 30 seconds to bet each round, then watch the ball roll
{% endstep %}
{% endstepper %}

### Blackjack

{% stepper %}
{% step %}
Sit at a blackjack table. There are 8 tables in three tiers: Junior (blue) $10 - $500, Normal (green) $500 - $10K and High (purple) $10K - $120K
{% endstep %}

{% step %}
Controls: `Enter` places the bet and hits, `Space` stands, `R` doubles, `E` splits and `F` surrenders
{% endstep %}

{% step %}
You get 20 seconds to bet and 30 seconds per turn before you are stood automatically. Blackjack pays 3:2 and the dealer stands on soft 17
{% endstep %}
{% endstepper %}

### Slots

{% stepper %}
{% step %}
Sit at any slot machine. Bets go from $10 to $1000. `Enter` spins and the arrow keys change the bet
{% endstep %}

{% step %}
Players standing nearby see your reels spin and hear the result too
{% endstep %}
{% endstepper %}

### Things Worth Checking

* Walk away or disconnect mid spin or mid hand. The round still finishes and your winnings arrive when you come back
* Two players at the same table and a third watching should all see the same cards, chips and wheel

***

## In-Game Creator

The lucky wheel prizes are built in game. No config editing needed.

{% stepper %}
{% step %}
Open the admin menu and go to Script Settings > Creator > Lucky Wheel
{% endstep %}

{% step %}
Add, edit or remove prizes. A prize can be cash, an item or a vehicle (with a paint pick), and each one has its own chance. The wheel holds up to 8 prizes
{% endstep %}

{% step %}
The rarest vehicle prize is shown on the casino podium
{% endstep %}
{% endstepper %}

Spin cost, spins per day, chip price, which balance the cashier uses (cash or bank), betting and turn timers, slot near miss chance and perk XP are all in the same menu under Script Settings > Casino.

***

## Good to Know

{% hint style="info" %}
Connected to [meteo-perks](../meteo-perks/): the casino perk line unlocks High Roller (+4% on winnings) and Casino VIP (+14% on winnings).
{% endhint %}

{% hint style="info" %}
The casino records house profit, wagers, payouts and big wins per game and per player. There is no menu for it - other scripts can read the numbers through exports.
{% endhint %}

{% hint style="success" %}
Lucky wheel spin cost and spins per day, slot near miss chance, blackjack betting and turn times, roulette betting time, chip price, which balance the cashier pays from (cash or bank) and perk XP per game are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Script Settings is god-tier only.

Add or edit lucky wheel prizes in-game with the **Lucky Wheel** creator.
{% endhint %}

{% content-ref url="../meteo-rewards/" %}
[meteo-rewards](../meteo-rewards/)
{% endcontent-ref %}
