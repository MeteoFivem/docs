---
description: >-
  Meteo crime tablet - crypto, achievements, blackmarket and groups script
  designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-crimetablet/
---

# Meteo Crime Tablet

This is a guide about testing the Meteo V2 crime tablet script designed exclusively for the Meteo V2 package. This is the tablet connected to all of our crime scripts and group system and more features you wont believe.

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

## Getting the Tablet

{% stepper %}
{% step %}
#### Teleport to the Location

Lets go to `/tp 901.9095, 3556.9412, 33.8196` and teleport
{% endstep %}

{% step %}
#### Get the Tablet

Point target and talk to him. You can buy the crime tablet from him for $2500 cash. Or you can spawn it using `/giveitem yourid meteo_crimetablet 1` or admin menu
{% endstep %}

{% step %}
#### Open the Tablet

Put your tablet to hotbar slot and open it
{% endstep %}

{% step %}
#### Set Your Crime Name

Enter a suitable crime name you want. Also this is possible to change later too
{% endstep %}

{% step %}
#### Explore Features

Check out all those things the tablet have. Make sure to check the exclusive testing video to get to know about all features

<figure><img src="../../../../.gitbook/assets/meteo_crimetablet.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
Also please note make sure you dont have 2 tablets in the inventory. Otherwise it will not work properly
{% endhint %}

***

## Testing Tablet Features

### Crypto

{% stepper %}
{% step %}
#### Add Test Crypto

Since we are testing lets just test the crypto and name change. First use `/addcrypto 50000`
{% endstep %}

{% step %}
#### Check Crypto

Open the tablet again after adding crypto. You can see the crypto. Go to crypto app and check out that
{% endstep %}

{% step %}
#### Test Name Change

Now go to settings and change your name and again go to crypto and see the transaction history and also amount must be removed from the full amount
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
`/addcrypto 50000` is an admin command. Check [test-commands](test-commands.md) for more info
{% endhint %}

### Achievements

{% stepper %}
{% step %}
#### Collect Achievements

Go to achievements and collect those newly unlocked achievements
{% endstep %}

{% step %}
#### Test All Achievements

Also if you really need to check whats happening after complete all achievements use `/setachievement all` command on chat and see lol. Now you can collect them forever lol
{% endstep %}

{% step %}
#### Refresh Tablet

After collecting all achievements close and open tablet so it will refresh with all crypto
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
`/setachievement all` only works on the showcase server. Dont get confused later
{% endhint %}

### Profile

* Also you can add profile pic and change name

### Blackmarket

{% stepper %}
{% step %}
#### Get a Rare Item

This is a feature of this crime tablet. Spawn rare item like `meteo_hqtable`. Use giveitem or admin menu
{% endstep %}

{% step %}
#### Create a Post

Go to blackmarket app and create post hq table on blackmarket. So other players can buy them and you will get crypto
{% endstep %}

{% step %}
#### Test Buying

Also try Buy from Shop and see if its showing correctly on map and get from the ped
{% endstep %}
{% endstepper %}

### Data File Exchange

* Go to `/tp 1469.9124, 6550.4980, 14.9041` and talk to The Fence
* You can sell a `meteo_datafile` for cash (you pay a small crypto fee) or trade it straight for crypto with no fee
* You get data files from [meteo-atmskimming](../meteo-atmskimming/)

### Groups

* You can see the group option on navbar of the tablet. You can either create one or join with an invite from a leader. Pretty simple
* Also this is built with all validations and auto group locking, player dead handling, logout handling all those possible scenarios :) to ensure your players will not get any issues ;)
* Nice. Check out groups and rankings with the testing video

### Terminal

* The terminal is where you run commands for things like atm skimming, boosting gps hack, vin scratch etc
* You can use commands like `ls` to list files, `cat` to read file contents, and create new files
* Check out the other crime script testing guides to see what terminal commands they use

### Services

* Go to services app to see all available crime services you can purchase with crypto
* Things like loose change, high speed drops, house robbery, vault jobs, hunts and more
* Check out their individual testing guides for how to use each one

***

## Also Check These Crime Scripts

Please check these other scripts since they all use the crime tablet. Each has their own testing guide:

{% content-ref url="../meteo-racing/" %}
[meteo-racing](../meteo-racing/)
{% endcontent-ref %}

{% content-ref url="../meteo-boosting/" %}
[meteo-boosting](../meteo-boosting/)
{% endcontent-ref %}

{% content-ref url="../meteo-loosechange/" %}
[meteo-loosechange](../meteo-loosechange/)
{% endcontent-ref %}

{% content-ref url="../meteo-hsd/" %}
[meteo-hsd](../meteo-hsd/)
{% endcontent-ref %}

{% content-ref url="../meteo-atmskimming/" %}
[meteo-atmskimming](../meteo-atmskimming/)
{% endcontent-ref %}

{% content-ref url="../meteo-organizations/" %}
[meteo-organizations](../meteo-organizations/)
{% endcontent-ref %}

{% content-ref url="../meteo-vaultjob/" %}
[meteo-vaultjob](../meteo-vaultjob/)
{% endcontent-ref %}

{% content-ref url="../meteo-transporthunt/" %}
[meteo-transporthunt](../meteo-transporthunt/)
{% endcontent-ref %}

{% content-ref url="../meteo-seahunt/" %}
[meteo-seahunt](../meteo-seahunt/)
{% endcontent-ref %}

{% content-ref url="../meteo-foresthunt/" %}
[meteo-foresthunt](../meteo-foresthunt/)
{% endcontent-ref %}

{% content-ref url="../meteo-bargehunt/" %}
[meteo-bargehunt](../meteo-bargehunt/)
{% endcontent-ref %}

{% content-ref url="../meteo-houserobbery/" %}
[meteo-houserobbery](../meteo-houserobbery/)
{% endcontent-ref %}

***

## Good to Know

{% hint style="success" %}
Black market fees and listable items, shop stock and restock time, data exchange payouts, tablet price, crypto settings and the name change fee are all editable in-game from **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Add or edit black market delivery drop points, the data file buyer and the tablet seller in-game with the Crime Tablet creator.
{% endhint %}
