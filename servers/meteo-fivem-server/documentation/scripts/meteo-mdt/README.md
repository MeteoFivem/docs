---
description: >-
  Meteo MDT - police mobile data terminal script
  designed exclusively for the meteo fivem server.
---

# Meteo MDT (Mobile Data Terminal)

This is a guide about testing the meteo fivem police MDT exclusively made for meteo server.

{% hint style="info" %}
get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

***

## Before You Start

* Access to the meteo test server
* Police job: `/setjob yourid police 4` (grade 4 is chief so you get full access including boss features)
* Open MDT using **Y** keybind

***

## Testing MDT Features

### Dashboard

* when you open MDT you will see the dashboard
* it shows reports assigned to you, latest reports, latest arrests, latest warrants and online police units

### Citizens Database

* go to citizens tab and search for a player by name, state id or phone number
* click on a citizen to see their full profile - personal info, warrant status, criminal history, vehicles owned

### Vehicles Database

* go to vehicles tab and search by plate, model name or owner name
* click on a vehicle to see its profile - owner info, status (out/garaged/impounded), stolen flags, officer notes
* try reporting a vehicle as stolen, marking as recovered, and adding officer notes

### Reports

* go to reports tab and create a new report
* report types: incident, investigative, FTO, personnel
* you can add title and description, add suspects with notes and charges, add victims, link vehicles and evidence lockers, assign officers, set incident date and due date
* reports auto save as you work
* try adding charges to a suspect - you can pick from the full penal code
* from a report you can also issue warrant or jail/fine a suspect directly

### Warrants

* go to warrants tab and issue a warrant for a citizen
* set expiry date and reason
* you can also create warrants from inside a report
* boss grade can delete warrants

### BOLOs (Be On the Lookout)

* go to bolos tab and create a new bolo
* you can make citizen bolos or vehicle bolos (by plate)
* add title, description, tags (DANGEROUS, ARMED, IMPORTANT, VIOLENT, FLEE RISK or custom tags)
* vehicle bolos work with [meteo-policeradar](../meteo-policeradar/) - radar will alarm when that plate is found

### Citations (Fines)

* you can issue citations from reports when jailing/fining a suspect
* go to citations tab to see all citations and filter by status (unpaid, paid, overdue)
* citizens can pay citations at city hall or courthouse NPCs using bank or cash
* paid fines go to police society bank account (if [meteo-banking](../meteo-banking/) is running)
* citations are overdue after 7 days (configurable)

### Jail/Fine System

* when processing a suspect from a report you can select charges, choose plea, add lawyer name, set jail time and fine amount, apply reduction and choose send to jail or fine only
* reduction limits by grade - cadet 10%, officer 25%, sergeant 50%, lieutenant 75%, chief 100%

### Penal Code

* go to penal code tab to browse all available charges
* 9 categories: violent crimes, drug offenses, weapons offenses, drug manufacturing, property crimes, fraud/forgery, traffic violations, disorderly conduct, DUI
* each charge has 3 levels: principal, accessory, conspiracy

### Activity Logs

* go to activity logs tab to see all MDT actions
* filter by type: warrants, reports, arrests, searches, citations, bolos, vehicles, jail

### Announcements

* boss grade can create department wide announcements with priority (normal, important, urgent)
* notifications show in the topbar with unread count badge

***

## Good to Know

* all settings like allowed jobs, citation due days, penal code charges, fine amounts, jail times, bolo tags and pagination are configurable on our config. you can change them once you get the server. we will guide you :)
* charge reduction limits per grade are configurable too
* connected with [meteo-policeradar](../meteo-policeradar/) for stolen vehicle alerts and [meteo-banking](../meteo-banking/) for citation payments
