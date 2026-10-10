---
description: >-
  Meteo banking - bank accounts, shared accounts, ATMs, bills, loans, taxes and
  economy logs script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-banking/
---

# Meteo Banking

This is a guide about testing the Meteo V2 banking script designed exclusively for the Meteo V2 package. Every money move from every Meteo script goes through this bank, so all of it shows up in the bank history and the admin economy logs.

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

## Testing Banking

{% stepper %}
{% step %}
**Bank**

Go to any bank location, point target and open the bank. You can create bank accounts (up to 5 per player, $250 fee taken from your bank). Deposit, withdraw and transfer money. Transfers can go to an account number, a state ID or a player ID
{% endstep %}

{% step %}
**Bank Locations**

* **Pillbox Hill** - `/tp 149.46, -1040.5, 29.37`
* **Alta Street** - `/tp 314.23, -278.83, 54.17`
* **Morningwood** - `/tp -1212.98, -330.78, 37.79`
* **Banham Canyon** - `/tp -2962.47, 482.93, 15.70`
* **Paleto Bay** - `/tp -112.22, 6469.91, 31.63`
* **Grand Senora** - `/tp 1175.07, 2706.63, 38.09`

These banks are placed in game now. Admins can move one, add more or take one off the map from the admin menu (Script Settings > Banking > Creator). No restart needed
{% endstep %}

{% step %}
**Shared Accounts**

Open one of your accounts and go to the Members tab, then Share access. The other player gets an invite and accepts it at a bank. You pick what they can do (view, deposit, withdraw, transfer, manage) and a daily limit for them
{% endstep %}

{% step %}
**Job, Gang and Business Accounts**

Bosses see their job and gang accounts in the bank. A boss can share access with lower grades from the Members tab. Business scripts (like dealerships and restaurants) keep their money in the bank too and show up under Business accounts for the people working there
{% endstep %}

{% step %}
**Activity Log**

Check the Activity log tab on any account. It shows who moved money, who changed access and blocked attempts. Every transaction also shows where it came from, and tax is shown on the payment when a purchase was taxed
{% endstep %}

{% step %}
**Loans**

Open the Loans page in the bank to see your open loans (like vehicle finance from dealerships), the payments left and when the next one is due. You can pay them from any account you can use
{% endstep %}

{% step %}
**ATMs**

Also check ATMs around the map. Point target and open. ATMs are for withdrawing from your accounts, deposits and transfers are only possible at a bank. ATM models are at gas stations, banks and around the city
{% endstep %}

{% step %}
**Giving Cash**

You can also point target to a player and give cash to them. This is part of banking
{% endstep %}

{% step %}
**Phone Bank App**

Open the Bank app on [meteo-phone](../meteo-phone/). You can check your accounts, transfer money, answer share invites and pay loans from anywhere. Bills also live here - send a bill to a player and they can pay or decline it from their phone. Cash in and out still needs a bank or an ATM
{% endstep %}
{% endstepper %}

> Make sure to check out the exclusive video for more details and see and check them out too

***

## Taxes

* The mayor sets the tax rates in the [meteo-mdt](../meteo-mdt/) (Government > Taxes), inside the limits admins set
* Taxes cover vehicle purchases and sales, shop purchases, restaurants, services, fuel and paychecks
* The collected tax goes into the mayor job's bank account, and the player sees the tax line on the transaction in the bank

***

## Admin Economy View

* Admins open the admin menu and go to Economy to see the whole economy: total money, all accounts and their logs
* Admins can freeze, close or adjust accounts from there
* Big transactions are flagged automatically for admin review under Flagged

***

## Admin Test Commands

{% hint style="warning" %}
`/bankapi` is a test command for checking the banking API. It is admin only (ace `command.bankapi`) and only exists when `Config.testCommands` is turned on. Keep it off on a live server.
{% endhint %}

* `/bankapi selftest` - runs the whole banking API on scratch accounts. Every line should say PASS
* `/bankapi stress 5000` - shows how fast it is and that the books add up
* `/bankapi` with no arguments lists every sub command (balance, add, remove, transfer, history, info, freeze, unfreeze, business, loans)

***

## Good to Know

{% hint style="success" %}
Account fees, the account limit, people per shared account, invite time and job account sharing are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add, move or remove banks in-game with the Banks creator on the same page. ATM models and the blip look stay on our config.
{% endhint %}

**Connected scripts:**

{% content-ref url="../meteo-bossmenu/" %}
[meteo-bossmenu](../meteo-bossmenu/)
{% endcontent-ref %}

{% content-ref url="../meteo-mdt/" %}
[meteo-mdt](../meteo-mdt/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}
