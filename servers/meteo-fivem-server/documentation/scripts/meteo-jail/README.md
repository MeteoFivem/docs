---
description: >-
  Meteo jail - prison with jobs, escape, solitary and visitation script
  designed exclusively for the meteo fivem server.
---

# Meteo Jail

This is a guide about testing the meteo fivem jail and prison script designed exclusively for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Know how to [spawn items](../../how-to-spawn-items.md)
* Familiar with [getting started](../../getting-started.md) basics

***

## Testing Jail

### Getting Jailed

* make sure you have the policejob to do this
* use command `/jail` and it will open a menu and enter your id and add like 10 months since we are just going to test
* also in this jail yourself is only working on testing server you to test the server. so once you get the server it will say you cant jail yourself. so dont panic

### After Getting Jailed

* check your inventory. it must clear all of your items
* `/tp 1790.8698, 2550.3269, 45.6732` to and interact with ped to see if you can free. only can free when your time is 0
* also `/tp 1840.4963, 2577.6892, 46.0143` to check visitation. you must check this with another player to check if you get notification when you have a visitor

### Prison Jobs

* `/tp 1779.62, 2560.86, 45.67` to teleport to dishwashing - talk with him and do the job and earn xp
* same for `/tp 1767.5349, 2498.7981, 45.8229` cleaning - also there are multiple locations for cleaning
* and also `/tp 1755.2362, 2549.3904, 40.1` repairs

### Prison Alarm and Meals

* also you can use `/testalarm` `/testmeal` command to check the meal and also prison alarm (please note these commands are only available on testing server. more info from [test-commands](test-commands.md))

### Solitary

* use `/solitary` on chat and enter your id and time in solitary
* also when solitary is over it will automatically update your location to normal prison
* also police can use `/updatesolitary`, `/unsolitary` commands too

### Other Commands

* also `/updatejail`, `/unjail` commands are available

### Getting Released

* when your time is over go to `/tp 1790.8698, 2550.3269, 45.6732` and interact and free
* after doing that you can get your belongings from `/tp 1838.0386, 2591.3049, 46.0143` and collect them

### Prison Activities

* `/tp 1776.9639, 2493.2446, 45.8222` to meditate and also use the prison gym. and also there is solitary gym too

***

## Testing Prison Escape

* go back again to jail
* first meet kitchen worker `/tp 1779.8843, 2545.7449, 45.6731`
* you need 5 cigarette to know the location of other guy. just spawn cigarette since we are testing. use /giveitem or spawn using admin menu
* after giving 5 cigarettes. he will give the location of other guy
* talk to him. but to talk with him you need rep. for normally players need to work on jobs and earn jail rep
* since testing. lets use `/setjailrep 1 500` command (note this command is only works on testing server and to learn about this check [test-commands](test-commands.md))
* talk to him again. now you can talk and get items from him. you can get useful items from him. also know the other guy location to do the prison break
* now you need 10 cigarettes to know the other guy location
* after give cigarettes go to that guy location
* now you need rep too. but since we used 500 its okay
* now we can get prison shovel. to do that we need metalscrap and steel
* lets `/giveitem metalscrap 5` and `steel 2` and get those items and craft. in normally players needs to smuggle those items to prison from contacts with burner phone
* then now you need 20 cigarette to know the escape path
* talk with that guy and give 20 cigarettes
* go to the marked location and use target and break with shovel
* after break prison alarm will activate. also police can use `/stopalarm` to stop the alarm
* all prison players now can escape until police will close the tunnel
* thats it. this is more advanced with doing with players and they have to find all those items and work together to pull this. thats how we designed this

***

## Good to Know

* all prison settings, job locations, escape requirements, solitary settings and rep rewards are configurable on our config. you can change them once you get the server. we will guide you :)
