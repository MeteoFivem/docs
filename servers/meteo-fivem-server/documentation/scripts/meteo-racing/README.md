---
description: >-
  Meteo racing - in-world track creator and multiplayer ELO racing, run from the
  crime tablet, designed exclusively for the meteo fivem server.
---

# Meteo Racing

This is a guide about testing the meteo fivem racing script designed exclusively for meteo server. Build your own tracks in the world and host multiplayer races with rankings and crypto prizes. It is fully connected with the [meteo crime tablet](../meteo-crimetablet/) - everything is managed from the tablet's Racing app.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* A [crime tablet](../meteo-crimetablet/) - the Racing app lives inside it
* Familiar with [getting started](../../getting-started.md) basics

***

## Building a Track (Admin)

{% stepper %}
{% step %}
**Open the Racing app**

Open your crime tablet and go to the Racing app, then choose "New track". Track creation, difficulty, the ranked flag and prize rules are admin only.
{% endstep %}

{% step %}
**Place checkpoints and props in-world**

The in-world editor drops you into a free cam. Place checkpoint gates (two-post gates the racers drive through) and decorate the track with barriers, cones, tyre walls and ramps.
{% endstep %}

{% step %}
**Set the rules and publish**

Back in the tablet, set the track's entry fee range, hosting fee, whether prizes are on, and whether it is a ranked or casual track. Publish it and it is ready to race.
{% endstep %}
{% endstepper %}

***

## Hosting and Joining a Race

{% stepper %}
{% step %}
**Host a lobby**

Pick a published track in the Racing app and host a lobby. You set the entry fee (within the track's range) and the max field size (up to 16 racers).
{% endstep %}

{% step %}
**Join and ready up**

Other players open the Racing app, join your lobby and pay the entry fee. Everyone stages at the start line and readies up.
{% endstep %}

{% step %}
**Start the race**

Once everyone is ready the host starts it. After a short countdown you are off. The winner takes the prize pot (a small house fee is taken off the top).
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Entry fees, hosting fees and prizes all use crime tablet crypto, not cash.
{% endhint %}

***

## During a Race

* Drive through each checkpoint gate in order - the next gate is marked for you
* You get a warning if you start heading the wrong way
* Other racers are ghosted so you cannot ram each other (ghosting turns off when a non-racer gets close, so bystanders can still interfere)
* You must drive a vehicle you own that matches the track's class requirement (classes S, A, B, C, D are worked out from the vehicle category and price)
* Keep the car you started in - it is locked by plate, so swapping cars starts a grace timer and can void your finish

***

## Rankings

* Ranked races affect your ELO rating
* Check the Racing app in the crime tablet for the leaderboard, your race history and your racing profile

***

## Good to Know

{% hint style="success" %}
Checkpoint size, class rules, lobby limits, the house fee, ghosting distance and all the race rules are configurable in our config. You can change them once you get the server. We will guide you :)
{% endhint %}
