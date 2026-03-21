---
description: >-
  Meteo perks - crime and civilian perk trees with 25 levels script
  designed exclusively for the meteo fivem server.
---

# Meteo Perks

This is a guide about testing the perks script designed exclusively for meteo server. Perks script is connected with almost every script :)

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

<figure><img src="../../../../.gitbook/assets/meteo-perks-preview.png" alt=""><figcaption></figcaption></figure>

***

## Before You Start

* Access to the meteo test server
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Perks

* Use f1 menu and open the perks menu
* You can choose any Specialization from crime and civilian
* There are 25 levels in total with daily XP caps (500 XP per day for each tree)

### Testing Crime Side

{% stepper %}
{% step %}
Lets choose **Light Hands** since its better for minigames
{% endstep %}

{% step %}
Use `/perksetlevel 1 crime 5` on chat and open perks again and see if its updated the level to 5

{% hint style="warning" %}
Note these commands are only available on our test server so you can check the server quickly. Also check out [test-commands](test-commands.md) for more details.
{% endhint %}
{% endstep %}

{% step %}
Lets open light hands that we chose earlier and unlock **Sharp Eyes**
{% endstep %}

{% step %}
Lets try search vehicles and dumpsters and you must see difference. Progress bar is more speed than before
{% endstep %}
{% endstepper %}

### Testing Civilian Side

{% stepper %}
{% step %}
Choose **Entrepreneur** since its for making money with our civ jobs
{% endstep %}

{% step %}
Use `/perksetlevel 1 civilian 3`

{% hint style="warning" %}
Note this command is only available on test server to check out features.
{% endhint %}
{% endstep %}

{% step %}
Open perks and go to Entrepreneur find **Budgeting** and unlock that
{% endstep %}

{% step %}
Lets go to shop and see item prices. Price must be lower than before
{% endstep %}
{% endstepper %}

### Money Washing (Crime Spec)

* Money washing is connected to your crime level
* Base rate is 40% conversion of meteo\_foldedcash to clean cash
* The rate goes up with crime level (40% at level 0, up to 90% at level 15)
* Daily caps also increase (from $10,000 to $500,000)
* Some perks give bonus rates too (kingpin +5%, blackmarket +5%, master +3%)

> Likewise with our test commands you can check each skills and see. Also all these rewards and percentages can be config once you get the server :)

***

## Good to Know

{% hint style="success" %}
All XP requirements, daily caps, perk bonuses, money washing rates and settings are configurable on our config. You can change them once you get the server. We will guide you :)
{% endhint %}

* Perks integrate with crime system, jobs, shops, minigames and more
* Jail time has passive bonuses for crime specialization (dig and cooldown reduction per level)
