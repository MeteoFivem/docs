---
description: >-
  Meteo boss menu - boss management, society banking and job applications with
  in-game creator script designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-bossmenuv2/
    - packages/meteo-v2-package/scripts/meteo-bossmenuv2/
---

# Meteo Boss Menu

This is a guide about testing the Meteo V2 boss menu script designed exclusively for the Meteo V2 package. This boss menu comes with in-game job applications, activity logs and an in-game creator, so boss menus are built in game instead of the config.

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

## Testing Boss Menu

### Police Boss Menu

{% stepper %}
{% step %}
First use `/setjob yourid police 4`

{% hint style="warning" %}
`/setjob` is a testing command and only works on our showcase server.
{% endhint %}
{% endstep %}

{% step %}
Go to `/tp -558.51, -125.61, 43.89` to go to the police boss menu location
{% endstep %}

{% step %}
Point target and open the police boss menu
{% endstep %}

{% step %}
The dashboard shows your employee count, the business balance and recent activity. From the Employees page you can hire players by server ID, change their grade or fire them
{% endstep %}

{% step %}
On the Banking page you can deposit and withdraw society money. This money is the job account on [meteo-banking](../meteo-banking/), so every move also shows in the bank history
{% endstep %}

{% step %}
All actions are saved in the Activity Logs page, and you can search and filter them
{% endstep %}
{% endstepper %}

### Job Applications

{% stepper %}
{% step %}
Bosses can turn applications on or off from the boss menu, and write their own questions for applicants
{% endstep %}

{% step %}
Go to `/tp -558.4874, -127.9775, 38` to check the application ped
{% endstep %}

{% step %}
Use `/setjob` to change to something else like ambulance first, since if you already have the job you can't submit a job application
{% endstep %}

{% step %}
Fill in the application and submit it. You can also check your application status at the same ped
{% endstep %}

{% step %}
Go back to the boss menu and accept or reject it from the Applications page. Applicants get phone notifications when accepted or rejected, and employees also get notified when they are hired, fired or their grade changes
{% endstep %}
{% endstepper %}

### Other Job Boss Menu Locations

* **Ambulance** - `/tp 68.8365, -352.0688, 43.9347`
* **Mechanic** - `/tp -324.3511, -130.1849, 43.9199`
* **Lawyer** - `/tp -1303.7463, -570.7798, 37.3764`
* **Judge** - `/tp -1286.9741, -590.4493, 34.3748`

### In-Game Creator

{% stepper %}
{% step %}
Open the admin menu and go to Script Settings > Creator > Boss Menu
{% endstep %}

{% step %}
Pick the job, give it a name and logo, then drop the menu points where bosses should open it. You can add as many points as you need
{% endstep %}

{% step %}
Set up the application desk: the ped, where it stands, and the lowest ranks that can review applications and write questions
{% endstep %}

{% step %}
Save it and it works right away. No restart and no config file. The job needs to exist in the core first, or the picker will not offer it
{% endstep %}

{% step %}
Boss menus you build can be exported, imported and saved as presets from the admin menu, so you can share them between servers
{% endstep %}
{% endstepper %}

> Check out the exclusive video for all details

***

## Good to Know

{% hint style="success" %}
Add or edit boss menus in-game with the Boss Menu creator in **Script Settings** in the admin menu ([meteo-manage](../meteo-manage/)) - which job, where it opens and the application desk. No code editing needed, and your changes survive script updates. Phone notification settings stay on our config.
{% endhint %}

{% content-ref url="../meteo-banking/" %}
[meteo-banking](../meteo-banking/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}
