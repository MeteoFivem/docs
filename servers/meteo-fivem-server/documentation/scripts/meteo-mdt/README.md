---
description: >-
  Meteo MDT - police mobile data terminal script
  designed exclusively for the meteo fivem server.
---

# Meteo MDT (Mobile Data Terminal)

This is a guide about testing the meteo fivem police MDT exclusively made for meteo server.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Police job: `/setjob yourid police 4` (grade 4 is chief so you get full access including boss features)
* Open MDT using **Y** keybind

***

## Testing MDT Features

### Dashboard

* When you open MDT you will see the dashboard
* It shows reports assigned to you, latest reports, latest arrests, latest warrants and online police units

### Citizens Database

{% stepper %}
{% step %}
Go to citizens tab and search for a player by name, state id or phone number
{% endstep %}

{% step %}
Click on a citizen to see their full profile - personal info, warrant status, criminal history, vehicles owned
{% endstep %}
{% endstepper %}

### Vehicles Database

{% stepper %}
{% step %}
Go to vehicles tab and search by plate, model name or owner name
{% endstep %}

{% step %}
Click on a vehicle to see its profile - owner info, status (out/garaged/impounded), stolen flags, officer notes
{% endstep %}

{% step %}
Try reporting a vehicle as stolen, marking as recovered, and adding officer notes
{% endstep %}
{% endstepper %}

### Reports

{% stepper %}
{% step %}
Go to reports tab and create a new report
{% endstep %}

{% step %}
Report types: incident, investigative, FTO, personnel
{% endstep %}

{% step %}
You can add title and description, add suspects with notes and charges, add victims, link vehicles and evidence lockers, assign officers, set incident date and due date
{% endstep %}

{% step %}
Reports auto save as you work
{% endstep %}

{% step %}
Try adding charges to a suspect - you can pick from the full penal code
{% endstep %}

{% step %}
From a report you can also issue warrant or jail/fine a suspect directly
{% endstep %}
{% endstepper %}

### Warrants

* Go to warrants tab and issue a warrant for a citizen
* Set expiry date and reason
* You can also create warrants from inside a report
* Boss grade can delete warrants

### BOLOs (Be On the Lookout)

* Go to bolos tab and create a new bolo
* You can make citizen bolos or vehicle bolos (by plate)
* Add title, description, tags (DANGEROUS, ARMED, IMPORTANT, VIOLENT, FLEE RISK or custom tags)
* Vehicle bolos work with [meteo-policeradar](../meteo-policeradar/) - radar will alarm when that plate is found

### Citations (Fines)

* You can issue citations from reports when jailing/fining a suspect
* Go to citations tab to see all citations and filter by status (unpaid, paid, overdue)
* Citizens can pay citations at city hall or courthouse NPCs using bank or cash
* Paid fines go to police society bank account (if [meteo-banking](../meteo-banking/) is running)
* Citations are overdue after 7 days (configurable)

### Jail/Fine System

* When processing a suspect from a report you can select charges, choose plea, add lawyer name, set jail time and fine amount, apply reduction and choose send to jail or fine only
* Reduction limits by grade - cadet 10%, officer 25%, sergeant 50%, lieutenant 75%, chief 100%

### Penal Code

* Go to penal code tab to browse all available charges
* 9 categories: violent crimes, drug offenses, weapons offenses, drug manufacturing, property crimes, fraud/forgery, traffic violations, disorderly conduct, DUI
* Each charge has 3 levels: principal, accessory, conspiracy

### Activity Logs

* Go to activity logs tab to see all MDT actions
* Filter by type: warrants, reports, arrests, searches, citations, bolos, vehicles, jail

### Announcements

* Boss grade can create department wide announcements with priority (normal, important, urgent)
* Notifications show in the topbar with unread count badge

***

## Good to Know

{% hint style="success" %}
All settings like allowed jobs, citation due days, penal code charges, fine amounts, jail times, bolo tags and pagination are configurable on our config. you can change them once you get the server. we will guide you :)
{% endhint %}

* Charge reduction limits per grade are configurable too

{% content-ref url="../meteo-policeradar/" %}
[meteo-policeradar](../meteo-policeradar/)
{% endcontent-ref %}

{% content-ref url="../meteo-banking/" %}
[meteo-banking](../meteo-banking/)
{% endcontent-ref %}

> Connected with meteo-policeradar for stolen vehicle alerts and meteo-banking for citation payments
