---
description: >-
  Meteo MDT - records terminal, dispatch and prison board for police, EMS,
  judges and lawyers designed exclusively for the Meteo V2 package.
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/scripts/meteo-mdt/
    - servers/meteo-fivem-server/documentation/scripts/meteo-dispatch/
    - packages/meteo-v2-package/scripts/meteo-dispatch/
---

# Meteo MDT

This is a guide about testing the Meteo V2 MDT exclusively made for the Meteo V2 package.

The MDT is not police only anymore. Police, EMS, judges, lawyers and the mayor all get their own view of it, and civilians get a public terminal with the parts everyone is allowed to see.

Dispatch now lives inside the MDT too. The old standalone meteo-dispatch script is gone - 911 calls, panic buttons, auto alerts and the dispatch console are all part of the MDT now, and the prison can be managed from it as well.

{% hint style="info" %}
Get access to our exclusive video testing guide on Discord to see all of this in action.
{% endhint %}

{% hint style="success" %}
Try it yourself for free on our showcase server. [See here to get access](../../how-to/how-to-access-showcase-server.md).
{% endhint %}

***

## Before You Start

* Access to the meteo showcase server
* Police job: `/setjob yourid police 4` (grade 4 is chief so you get full access)
* Open the MDT with **F5** or `/mdt`
* You need to be on duty. Clock in at the station first
* If the MDT ever acts up after a long session, `/reloadmdt` soft-reloads the interface

{% hint style="info" %}
Want to see the other side of it? Try `/setjob yourid ambulance 4` for the medical view, `/setjob yourid judge 0` for the court view and `/setjob yourid lawyer 0` for the attorney view. Each one opens a different set of tabs.
{% endhint %}

***

## Testing MDT Features

### Dashboard

* When you open the MDT you land on the dashboard
* Widgets show open reports, active warrants, active BOLOs, most wanted, upcoming hearings, recent reports and your own recent activity
* The radio panel is here too - see [Radio](#radio) below

### Dispatch

All alerts land on the **Dispatch** page of the MDT and pop up on screen (top right) for every on-duty player of the jobs the alert is meant for.

{% stepper %}
{% step %}
Set your job to `/setjob yourid police 4` or `/setjob yourid ambulance 4` and clock in
{% endstep %}

{% step %}
Get a second player to send an alert (or use `/testalert`, see below). It pops up on your screen with a sound
{% endstep %}

{% step %}
Press **J** to respond. You get a blip with a GPS route that clears once you arrive, stop responding or the call closes. Use the **Left** and **Right** arrow keys to move between alerts in the queue
{% endstep %}

{% step %}
Open the MDT and go to the Dispatch page. Switch between **Live**, **Mine** and **History**, and search calls by code, street, caller or unit
{% endstep %}

{% step %}
Open a call to see its details, the live map, the responding units (en route or on scene) and a timeline of everything that happened on it
{% endstep %}

{% step %}
From a call you can respond, set GPS, message the caller, assign other units and close the call
{% endstep %}
{% endstepper %}

* Repeat reports of the same thing close together fold into the open call as "3 reports" instead of spamming new calls
* Calls nobody touches close on their own after a while
* Messaging a caller sends it to their meteo-phone from Emergency Dispatch (911)
* Open **Alert settings** on the Dispatch page to turn popups and sounds on or off, change the volume and pick which alert types pop up or play a sound. Panic alerts always show
* Sergeant and up (and senior EMS) get the full-screen **Dispatch Console** with **F6** or `/dispatch` - every call and every unit on one screen

### Making a 911 Call (As Civilian)

* You need a `phone` in your inventory to call
* Your character puts the phone to their ear for a few seconds before the call goes through. Getting knocked down or cuffed drops the call
* Use these commands on chat:
  * `/911 your message here` - emergency call (police and EMS)
  * `/911e your message here` - medical emergency (police and EMS). Works even while you are downed
  * `/911a your message here` - anonymous tip (police, your name and number are hidden)
  * `/311 your message here` - non-emergency call (police)

### Panic Buttons (As Police/EMS)

* `/panic` or `/10-99` - officer down (red panic alert that stays until someone responds)
* `/10-78` - officer needs assistance
* You can also send these from the radial menu
* You need to be on duty with dispatch access, and there is a short cooldown between presses

### Auto Alerts

* Shooting a weapon sends a shots fired alert written like a witness report - weapon type, how many shots and a description of the shooter
* Shooting from a vehicle sends a drive-by alert with the vehicle, colour, heading and sometimes the plate (witnesses do not always catch the full plate)
* Silenced weapons and on-duty police do not trigger alerts, and there is a cooldown per player
* Other scripts (store robberies, house robberies, vehicle theft, drug sales and more) send their own alerts into the same system

{% hint style="warning" %}
**Showcase server only** - `/testalert [preset]` sends a test alert at your position (a random one if you leave the preset out). It is admin only and is there so you can test dispatch on your own.
{% endhint %}

### Search

{% stepper %}
{% step %}
Go to the search tab and type anything - a name, State ID, plate, weapon serial, case number or tag
{% endstep %}

{% step %}
It searches every record you have access to at once - citizens, vehicles, reports, weapons, warrants, licenses, fingerprints, lab reports, master files and tags
{% endstep %}

{% step %}
Filter by type using the dropdown if you get too many results
{% endstep %}
{% endstepper %}

### Citizen Records

* Search a citizen and open their profile
* Tabs on a profile: personal info, convictions, reports, vehicles, properties, weapons, licenses, fines, tickets and prescriptions
* Personal info includes date of birth, gender, nationality, phone, blood type, occupation and whether their fingerprint is on file
* Add officer notes, attach tags, mark them wanted or clear the wanted flag

{% hint style="info" %}
Deleted characters stay on file. The record is kept and still linked to their reports, warrants and court filings so old cases do not break.
{% endhint %}

### Vehicle Records

* Search by plate, model or owner
* Vehicle profile shows owner, status (out, garaged, impounded), stolen and seized flags and officer notes
* Report a vehicle stolen, mark it recovered and add notes
* Vehicle BOLOs work with [meteo-policeradar](../meteo-policeradar/) - the radar alarms when that plate passes

### Weapon Registry

{% stepper %}
{% step %}
Open a citizen's profile while they are near you and holding a weapon, then use **Register Weapon**
{% endstep %}

{% step %}
The weapon is logged with its serial, type, attachments, where it was registered and who registered it
{% endstep %}

{% step %}
Search that serial later to pull the full history - owner changes, stolen reports, seizures and unregistrations
{% endstep %}

{% step %}
Try flagging one as stolen or seized, then clearing the flag. Weapons registered through the police armory or a gun shop show up here automatically
{% endstep %}
{% endstepper %}

### Reports

{% stepper %}
{% step %}
Go to reports and create a new one. Types are incident, investigative, FTO and personnel
{% endstep %}

{% step %}
Add a title and description with the rich text editor - bold, headings, lists, quotes, colours, mentions and images pulled from the photo reel
{% endstep %}

{% step %}
Add suspects with notes and charges, add victims, add tasks, and link vehicles, weapons, properties, evidence lockers, lab reports and other reports
{% endstep %}

{% step %}
Assign officers, set the incident date and due date. Reports auto save as you work and lock while someone else is editing
{% endstep %}

{% step %}
From a report you can issue a warrant or book a suspect directly
{% endstep %}
{% endstepper %}

### Booking (Jail and Fines)

* Booking a suspect from a report opens the charge sheet
* Select charges, choose a plea (no contest, not guilty, guilty), add a lawyer name, set jail time and fine amount
* Apply a reduction to the jail time and fine - only roles with the sentence reduction permission can do this
* Choose jail plus fine, or fine only
* Jail time sends the suspect straight to [meteo-jail](../meteo-jail/). The suspect has to be online for jail time, a fine only sheet can still be booked while they are offline

### Penal Code

* Browse every charge in the penal code tab
* 9 categories: violent crimes, drug offenses, weapons offenses, drug manufacturing, property crimes, fraud and forgery, traffic violations, disorderly conduct and DUI
* Each charge has 3 levels - principal, accessory and conspiracy - with its own fine and jail time

### Warrants

* Issue arrest or search warrants against a person, vehicle, phone or property
* Set the grounds, authorizing judge and expiry
* Warrants can also be created from inside a report
* Print a physical copy - see [Printed Documents](#printed-documents)

### Wanted and BOLO

* Mark a citizen wanted with a reason - they show on the dashboard most wanted list and on the public terminal
* Post BOLOs for citizens, vehicles or weapons with details and tags
* Resolve a BOLO once it is done

### Court Docket

{% stepper %}
{% step %}
Set yourself to `judge` or `lawyer` and open the court docket tab
{% endstep %}

{% step %}
Create a filing - criminal or civil - with a case number, title and description
{% endstep %}

{% step %}
Add defendants, plaintiffs and witnesses. Charges pull in from any linked reports, or add them manually
{% endstep %}

{% step %}
Assign a presiding judge and a lawyer, schedule hearings and watch them appear on the calendar view and the dashboard
{% endstep %}

{% step %}
Post updates to the filing, add court notes and attach photos
{% endstep %}
{% endstepper %}

### Laboratory

This replaces the old standalone fingerprint scanner. Forensics now run as real lab work with a queue.

{% hint style="warning" %}
**The lab work is not done inside the MDT.** You do it in the world, standing at the lab bench and the evidence intake, using the target menus there. The Laboratory tab in the MDT is where the finished reports get read - it does not process anything.
{% endhint %}

{% hint style="info" %}
Lab benches, evidence intakes and the public records clerk are placed with the MDT Places creator in the admin menu, so you can add more or move them without touching the config.
{% endhint %}

**At the lab bench** - `/tp -543.46, -121.92, 43.86`

Target the bench and the menu gives you:

| Option | What it does |
| ------ | ------------ |
| Upload Fingerprints | Files every fingerprint card you are carrying, no order needed |
| Register Lab Order | Opens a new case folder with its own evidence stash |
| Lab Orders | Work your open folders - open the stash, start processing, rename, cancel or close |

**At the evidence intake** - `/tp -540.98, -118.86, 43.86`

Target the intake and you can open the drop box or upload everything in it. The box only accepts lab reports.

**In the MDT** - the Laboratory tab lists every report that made it through intake. Open one to see the evidence in it, what it matched, the lab notes and the analysis history.

### Testing the Full Lab Run

{% stepper %}
{% step %}
Get a `meteo_fingerprint_kit` and use it near a suspect to lift their print onto a `meteo_fingerprint_card`. One kit does 10 prints
{% endstep %}

{% step %}
Go to the lab bench, target it, and register a lab order with a case label
{% endstep %}

{% step %}
Open that order's stash from the same menu and drop your filled evidence bags in
{% endstep %}

{% step %}
Choose **Start Processing**. The order goes in the queue and the report is ready after a short wait
{% endstep %}

{% step %}
Collect the finished `meteo_lab_report` from the order, then walk to the evidence intake and upload it
{% endstep %}

{% step %}
Now open the MDT and go to the Laboratory tab to read what it matched
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Reports track evidence quality. A degraded sample gives no DNA, a partial or smudged print may not match, and a scratched serial gives no weapon. You can re-run an analysis later once more records exist, and the run history shows whether anything new matched.
{% endhint %}

* The lab is gated by job and duty rather than by an MDT permission, so you need to be on duty in an allowed job to use the bench at all
* Only filled evidence bags go in a lab order, and an order locks once it is in the queue
* Boss grade can expunge a fingerprint from record with a reason

### Licenses

Every license in the city lives in the MDT, including the driver's and weapons licenses that used to come from city hall.

* The server ships with two **obtainable** license types:

| License | Serial | Price |
| ------- | ------ | ----- |
| Driver's License | `LIC-DL-7K3M9` | $350 |
| Weapons License | `LIC-WL-4Q8XR` | $750 |

* Create more license types in the licenses tab - name, description, card image and price. The mayor can create license types by default
* Tick **Obtainable** on a type and citizens can buy it themselves at [meteo-cityhall](../meteo-cityhall/). The name and price shown at city hall come straight from the MDT
* Issue, suspend, reinstate or revoke a license on a citizen's profile, each with an audit trail. By default a sergeant can suspend and revoke, and a lieutenant and up can also issue
* A revoked license is final and cannot be reinstated, a suspended one can

{% stepper %}
{% step %}
Clear your job with `/setjob yourid unemployed 0` and buy a driver's license at city hall
{% endstep %}

{% step %}
You get a `meteo_license` card. One item covers every license type - the license, holder and status are printed on each card
{% endstep %}

{% step %}
Use the card to show it to players standing close to you
{% endstep %}

{% step %}
Now set yourself back to police, suspend that license from your profile in the MDT and show the card again. It reads as suspended, because the card re-checks the live status every time
{% endstep %}

{% step %}
Drop or lose the card and go back to city hall - you can get a replacement card for $75 as long as you still hold the license. This works for officer-issued licenses too
{% endstep %}
{% endstepper %}

### Tickets

* Create ticket types in the tickets tab with a default fine and a hard maximum the server enforces
* Issue tickets from a citizen's profile, then mark them paid, unpaid or void
* Citizens pay their fines and tickets at the city hall or courthouse NPC, or on the public terminal

### Beds and Prescriptions

Set yourself to EMS with `/setjob yourid ambulance 4` for these.

* **Beds** shows live hospital bed occupancy per ward, with patient condition (stable, recovering, critical) and how long they have been admitted
* **Prescriptions** lists everything written across every patient. Write a new one to a patient and filter by active, expired or cancelled

### Roster

* Shows department personnel - members, rank, callsign, duty status, strikes and praises
* Hire citizens straight into the department, change ranks and fire members
* You cannot manage someone of equal or higher rank, or change your own rank
* A member profile shows their 30 day duty heatmap, statistics (tickets, reports, fines, jail time, impounds) and their activity logs from evidence, laboratory, armory, garage and prison

### Photo Reel

{% stepper %}
{% step %}
Get a `meteo_camera` and use it in the field. Left click captures, scroll zooms
{% endstep %}

{% step %}
The photo lands in the MDT photo reel under the Camera category
{% endstep %}

{% step %}
Add photos manually by URL too, and organise everything with your own categories
{% endstep %}

{% step %}
Use **Locate** on a photo to mark where it was taken on your map
{% endstep %}
{% endstepper %}

* Photos can be attached to reports, court filings and person records
* Mugshots pushed in by other scripts show up here as well

### Printed Documents

Everything important can leave the MDT as a real item someone can read in hand.

| Document | What you need | What it is |
| -------- | ------------- | ---------- |
| Citation | `meteo_ticketbook` | Notice to appear with the violation, fine and court date |
| Wanted poster | `meteo_caseforms` | Printed wanted notice or BOLO sheet |
| Warrant | `meteo_caseforms` | Signed arrest or search warrant |

* A ticket book holds 25 pages and a form pad holds 25 sheets. Printing tears one out
* Use the printed item to read it. Press **ESC** to put it away
* Printed papers re-check the record, so a cleared wanted flag reads as no longer wanted

### Tags

* Create your own tags with a name, colour and scope (persons, vehicles or both)
* Attach them to records and then search by tag later

### Sharing Records

* Use **Share** on a report or court filing to give specific people view, edit or post access
* You can only grant access your own role holds
* Recipients see it under **Shared with Me** in their sidebar plus a notification
* Sharing grants access to that one record, not to the MDT itself

### Radio

* Managed radio channels live on the dashboard
* Create a channel with a name like TAC-1, see who is connected and mute individual members
* Works together with [meteo-radio](../meteo-radio/)

### Announcements and Notifications

* Boss grade can post department wide announcements with a priority (normal, important, urgent)
* Notifications sit in the topbar with an unread badge. Mark them read one at a time or all at once

### Prison

Manage inmates straight from the MDT. This needs [meteo-jail](../meteo-jail/) running.

{% stepper %}
{% step %}
Book a suspect with jail time from a report (or use a second player) so someone is serving time
{% endstep %}

{% step %}
Open the **Prison** page. You see everyone serving, how much time is left, their progress and whether they are inside, outside the walls or offline
{% endstep %}

{% step %}
Filter by online, solitary or awaiting release, or search by name or State ID
{% endstep %}

{% step %}
Pick an inmate to see their sentence (sentenced, served, taken off) and their prison reputation
{% endstep %}

{% step %}
Try the actions - change the sentence, send to solitary or take them out, and release early
{% endstep %}
{% endstepper %}

* The facility tiles let you call a meal run and raise or stop the prison alarm
* The prison can only act on inmates who are connected, so offline inmates are read only
* What you can do depends on your rank. By default every officer can view the board, sergeant and up can work the alarm, and the chief can release early

### Taxes

The city's tax system is run from the MDT under **Government > Taxes**. [meteo-banking](../meteo-banking/) only applies the rates and pays the tax into the `mayor` job account.

{% stepper %}
{% step %}
Set yourself to `/setjob yourid mayor 0` and open the Taxes page
{% endstep %}

{% step %}
Each tax shows its current rate, its allowed range and exactly what it applies to
{% endstep %}

{% step %}
Move a rate and press **Apply**. An announcement goes out to everyone with the old and new rate
{% endstep %}

{% step %}
Try changing the same tax again - it is on a 60 minute cooldown before it can be changed again
{% endstep %}

{% step %}
Buy something that is taxed, like fuel at a pump, and check the `mayor` job account in meteo-banking to see the tax land there
{% endstep %}
{% endstepper %}

| Tax | Applies to | Starting rate | Range |
| --- | ---------- | ------------- | ----- |
| Vehicle Purchase | Buying a vehicle at a dealership | 5% | 0 - 15% |
| Vehicle Sale | Selling a vehicle back to a dealership and private sales on the phone | 3% | 0 - 10% |
| Shop Purchase | Stores marked as taxed in the shop creator | 5% | 0 - 15% |
| Restaurant | Restaurant shop purchases, paid counter orders and supplier orders | 5% | 0 - 15% |
| Services | Benny's mods and work orders, mechanic invoices and hospital check-in | 5% | 0 - 15% |
| Fuel | Fuel and jerrycans at the pump | 5% | 0 - 15% |
| Income | Taken from paychecks | 5% | 0 - 25% |

* The mayor can only move a rate inside its range. Changing the range itself is a separate permission that no role has by default - give it to a role in Role Management
* A tax only shows up when the scripts that charge it are running, and the whole page needs meteo-banking running
* Other scripts read the live rates through the [tax exports](exports.md#taxes)

### Logs

* **Audit logs** record every action taken in the MDT
* **Activity logs** record per citizen activity pushed in by other scripts - evidence, laboratory, armory, garage and prison - and show on roster member profiles

### Public Terminal

{% stepper %}
{% step %}
Clear your job with `/setjob yourid unemployed 0`
{% endstep %}

{% step %}
Go to `/tp -1293.72, -570.54, 30.57` and target the public records clerk
{% endstep %}

{% step %}
As a civilian you get the public record - announcements, the penal code and the public wanted list
{% endstep %}

{% step %}
Target the same ped for **Fines & Tickets** to pay what you owe with cash or bank
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Off duty officers fall back to this same public view, so the job side of the MDT only opens when you are clocked in.
{% endhint %}

### Roles and Permissions

{% stepper %}
{% step %}
Go to settings and open **Role Management** (admin only by default)
{% endstep %}

{% step %}
A role is matched on an exact job and grade, so every rank that needs access gets its own role
{% endstep %}

{% step %}
Pick exactly which permissions that role holds. Copy and paste permission sets between roles to build ranks quickly
{% endstep %}

{% step %}
The **Everyone** role applies to every player on top of their job role - that is what makes the public terminal work
{% endstep %}

{% step %}
Use **View As Role** to preview the MDT exactly as any role sees it, so you can check a rank before handing it out
{% endstep %}
{% endstepper %}

The server ships with roles for police (recruit to chief), EMS (recruit to chief), judge, lawyer and mayor.

### Settings

* Set your own profile photo and toggle whether the MDT dims and frees your cursor when the mouse leaves the window

***

## Good to Know

{% hint style="success" %}
Add or edit public records clerks, lab benches and evidence intakes in-game with the MDT Places creator in the admin menu ([meteo-manage](../meteo-manage/)) - no code editing needed, and your changes survive script updates. Creators are god-tier only.
{% endhint %}

{% hint style="info" %}
Allowed jobs, keybinds, dispatch alerts, call commands, alert sounds, auto alert triggers, lab timings, ticket books, license cards, log retention and paperwork headers are configurable on our config. You can change them once you get the package. We will guide you :)
{% endhint %}

* Who can reduce sentences, open the dispatch console or manage the prison is set per role in Role Management
* Callsigns are managed from the roster
* Profile and photo image URLs are checked against an allowed host list, so nobody can paste a random link
* Logs are kept for 30 days by default and old rows are cleared on server start

{% content-ref url="../meteo-policejob/" %}
[meteo-policejob](../meteo-policejob/)
{% endcontent-ref %}

{% content-ref url="../meteo-evidence/" %}
[meteo-evidence](../meteo-evidence/)
{% endcontent-ref %}

{% content-ref url="../meteo-policeradar/" %}
[meteo-policeradar](../meteo-policeradar/)
{% endcontent-ref %}

{% content-ref url="../meteo-medicaljob/" %}
[meteo-medicaljob](../meteo-medicaljob/)
{% endcontent-ref %}

{% content-ref url="../meteo-jail/" %}
[meteo-jail](../meteo-jail/)
{% endcontent-ref %}

{% content-ref url="../meteo-banking/" %}
[meteo-banking](../meteo-banking/)
{% endcontent-ref %}

{% content-ref url="../meteo-phone/" %}
[meteo-phone](../meteo-phone/)
{% endcontent-ref %}

> Connected with meteo-evidence for lab analysis, meteo-policeradar for plate alerts, meteo-medicaljob for beds, meteo-jail for booking and the prison board, meteo-banking for fine payments and taxes, and meteo-phone for dispatch replies. Crime scripts send their alerts straight into MDT dispatch
