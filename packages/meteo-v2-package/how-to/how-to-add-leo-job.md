---
description: >-
  Add a new LEO-type job (BCSO, Sheriff, State Police, etc.) to the meteo
  server.
icon: shield-halved
metaLinks:
  alternates:
    - servers/meteo-fivem-server/documentation/how-to/how-to-add-leo-job.md
---

# How to Add a LEO Job

This guide lists every place you need to touch when adding a new LEO-type job (e.g. BCSO, Sheriff, State Police). Replace `bcso` in the examples with your new job name.

A lot of this is done in game now. Open the admin menu with **F9** (or `/admin`) and go to **Script Settings**. Settings for a script sit under its name, and anything you place in the world (garages, boss menus, lockers, shops) is under **Script Settings** > **Creator**. Everything else is still a `shared/config.lua` change.

***

## 1. Define the job

**File:** `resources/[meteostudios]/meteo-core/shared/jobs.lua`

Add a new entry alongside `police`. The `type = 'leo'` field is what makes our scripts treat it as law enforcement. Job names must be lowercase.

```lua
['bcso'] = {
    label = 'Blaine County Sheriff',
    type = 'leo',
    defaultDuty = true,
    offDutyPay = false,
    grades = {
        [0] = { name = 'Cadet', payment = 50 },
        [1] = { name = 'Deputy', payment = 75 },
        [2] = { name = 'Sergeant', payment = 100 },
        [3] = { name = 'Lieutenant', payment = 125 },
        [4] = { name = 'Sheriff', isboss = true, bankAuth = true, payment = 150 },
    },
},
```

Restart the server after saving so the core picks up the new job. Once it exists, it shows up in every job picker in the admin menu, and anything that checks `job.type == 'leo'` works on its own (cop counts for robberies and crime tablet jobs, the police radial menu, evidence and fingerprint checks). The steps below cover the places that still list job names.

***

## 2. Police stations, armory and cameras

Done in game. Open the admin menu (F9) > **Script Settings** > **Police** > **Access** and add `bcso` to **Supported jobs**.

Every police station, armory and camera works for every job in this list, so BCSO can use the existing Mission Row station straight away. If you want a separate sheriff station, place it in **Script Settings** > **Creator** > **Police** and set **Type** to **Police station**.

***

## 3. Evidence lockers

Done in game. Open the admin menu (F9) > **Script Settings** > **Evidence** > **Access** and add `bcso` to **Supported jobs**.

***

## 4. MDT forensics lab access

**File:** `resources/[meteostudios]/meteo-mdt/shared/config.lua`

The lab is gated by job and duty rather than by an MDT permission, so it has its own list:

```lua
Config.lab = {
    allowedJobs = { 'police', 'bcso' },
    requireDuty = true,
    ...
}
```

***

## 5. MDT access

MDT access is not a config list - it runs on roles stored in the database, so you set this up in game.

{% stepper %}
{% step %}
Open the MDT and go to **Settings - Role Management** (admin only)
{% endstep %}

{% step %}
Create a role for each BCSO grade. A role matches on an exact job and grade, so grade 0, 1, 2 and so on each need their own role
{% endstep %}

{% step %}
**Copy** the permissions from the matching police rank and **Paste** them onto the BCSO role, then adjust from there
{% endstep %}

{% step %}
Leave **Requires on-duty** ticked so the job side of the MDT only opens when they are clocked in
{% endstep %}

{% step %}
Use **View As Role** to check what the new role can actually see before you hand it out
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The **Everyone** role applies to all players on top of their job role, so you do not need to touch it for a new LEO job.
{% endhint %}

***

## 6. Dispatch (911 calls and alerts)

**File:** `resources/[meteostudios]/meteo-mdt/shared/config.lua`

Dispatch is part of meteo-mdt. An alert only reaches on-duty players whose job is named on that alert, so add `bcso` everywhere `police` is listed inside `Config.dispatch`:

```lua
Config.dispatch = {
    defaultJobs = { 'police', 'bcso' }, -- used when an alert names no jobs
    ...
    calls = {
        ['911'] = { code = '911', title = '911 Call', priority = 'high', jobs = { 'police', 'bcso', 'ambulance' } },
        ['311'] = { code = '311', title = '311 Non-Emergency', priority = 'low', jobs = { 'police', 'bcso' } },
        ...
    },
    presets = {
        shooting = { code = '10-71', title = 'Shots Fired', priority = 'medium', jobs = { 'police', 'bcso' } },
        storerobbery = { code = '10-65', title = 'Store Robbery', priority = 'high', jobs = { 'police', 'bcso' } },
        officerdown = { code = '10-99', title = 'Officer Down', priority = 'high', jobs = { 'police', 'bcso', 'ambulance' }, panic = true },
        ...
    },
    shooting = {
        ignoreJobs = { 'police', 'bcso' }, -- their own gunfire does not raise a shots fired alert
        ...
    },
}
```

Go through every entry in `calls` and `presets`, not just the ones shown above.

***

## 7. Phone emergency lines

**File:** `resources/[meteostudios]/meteo-phone/shared/config.lua`

If calling 911 or 311 from the phone should ring BCSO too, add the job to `Config.services`:

```lua
Config.services = {
    emergency = {
        { job = 'police', number = '911' },
        { job = 'bcso', number = '911' },
        { job = 'ambulance', number = '911' },
    },
    lines = {
        ['911'] = { 'police', 'bcso', 'ambulance' },
        ['311'] = { 'police', 'bcso' },
    },
    ...
}
```

***

## 8. Crime alerts from other scripts

Many crime scripts send their own dispatch alert with a job list. Add `bcso` to each one you want BCSO to hear about:

| File (under `resources/[meteostudios]/`) | Variable |
| --- | --- |
| `meteo-atmskimming/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-bargehunt/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-boosting/shared/config.lua` | `Config.dispatch.jobs`, `Config.guardFleeDispatch.jobs`, `Config.gpsTracker.policeJobs` (who sees the GPS tracker) |
| `meteo-foresthunt/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-graveyarddig/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-houserobbery/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-hsd/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-hussling/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-loosechange/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-seahunt/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-transporthunt/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-vaultjob/shared/config.lua` | `Config.dispatch.jobs` |
| `meteo-jail/shared/config.lua` | `Config.escapeSystem.dispatch` - the `jobs` in `tunnelOpened`, `prisonBreak` and `escapeAttempt` |
| `meteo-chopshop/shared/config.lua` | `Config.allowedJobs` |
| `meteo-properties/shared/config.lua` | `Config.lockpick.policeJobs` (break-in alerts and the on-duty cop count) |

Most of them look like this:

```lua
Config.dispatch = {
    ...
    jobs = { 'police', 'bcso' },
}
```

meteo-chopshop uses a keyed table instead:

```lua
Config.allowedJobs = {
    ['police'] = true,
    ['bcso'] = true,
}
```

{% hint style="info" %}
A few small alerts are fixed to `police` and cannot be changed: drug sales, pickpocketing, mailbox and parking meter robbery, vehicle searching, car break-ins from meteo-vehiclekeys, and the call for help from a downed player in meteo-medicaljob. BCSO can still see these calls in the MDT dispatch page if their MDT role has the **See All Departments** permission.
{% endhint %}

***

## 9. Police radar

Done in game. Open the admin menu (F9) > **Script Settings** > **Police Radar** > **Alerts** and add `bcso` to **Allowed jobs**. These jobs get the radar's BOLO and stolen plate alerts.

***

## 10. Jail (jail/unjail permission)

Done in game. Open the admin menu (F9) > **Script Settings** > **Jail** > **Sentence** and add `bcso` to **Jobs that can jail**.

***

## 11. Restricted radio channels

**File:** `resources/[meteostudios]/meteo-radio/shared/config.lua`

If you lock radio channels to jobs, add BCSO to the channels it should share:

```lua
Config.restrictedChannels = {
    [1] = { 'police', 'bcso', 'ambulance' },
}
```

***

## 12. Job garage (vehicles)

Done in game. Open the admin menu (F9) > **Script Settings** > **Creator** > **Job Garages**. Either open an existing police garage and add a row for `bcso` under **Who Can Use It** > **Jobs** so both jobs share it, or **Duplicate** the police garage and set the copy to `bcso` with its own fleet and parking bays. A duplicated garage starts switched off, so turn it on when you are done.

Vehicles handed out by a job garage get shared keys for that job automatically.

***

## 13. Boss menu (society management)

Done in game. Open the admin menu (F9) > **Script Settings** > **Creator** > **Boss Menu** and add a new boss menu:

* **Job** - pick `bcso`
* **Name** - shown at the top of the menu, e.g. `Blaine County Sheriff`
* **Menu points** - stand where the sheriff should open it and add the point
* **Job applications** - optional, set the desk and the ranks that review applications

Only bosses of the job (`isboss = true` grades) can open it.

***

## 14. Job locker (uniforms)

Done in game. Open the admin menu (F9) > **Script Settings** > **Creator** > **Appearance**, add a place with **Type** set to **Job locker** and **Job** set to `bcso`, then place it in the sheriff station.

Uniforms are saved per job, not per locker. Have a BCSO boss walk up to the locker in the outfit they want and add it - every BCSO member can then pick it from any BCSO locker.

***

## 15. Shops (job-restricted items)

Done in game. Open the admin menu (F9) > **Script Settings** > **Creator** > **Shops** and open the shop that sells police items. Under **Stock** > **Products**, the **Job** column limits who can buy a row - add BCSO next to police, separated by a comma:

```
police, bcso
```

A **Job** set on a branch under **Locations** > **Branches** works the same way and limits the whole branch.

***

## 16. City Hall (police badge)

**File:** `resources/[meteostudios]/meteo-cityhall/shared/config.lua`

The police badge document is only shown to the jobs in its `jobs` list. Add BCSO if they should be able to buy it:

```lua
Config.documents = {
    ...
    policeBadge = {
        itemName = 'meteo_policebadge',
        label = 'Police Badge',
        icon = 'shield',
        price = 100,
        jobs = { 'police', 'bcso' },
    },
}
```

Optionally add the job to the City Hall job directory too. `coords` is optional and adds a GPS button:

```lua
Config.whitelistedJobs = {
    { type = 'police', name = 'Los Santos Police Department', icon = 'shield', category = 'Law Enforcement', coords = vec4(441.0, -981.0, 30.7, 90.0) },
    { type = 'bcso', name = 'Blaine County Sheriff', icon = 'shield', category = 'Law Enforcement' },
    ...
}
```

***

## 17. Buffs (stress whitelist)

**File:** `resources/[meteostudios]/meteo-buffs/shared/config.lua`

Jobs in this list never gain stress. Add BCSO if they should be exempt like police:

```lua
Config.stress = {
    enabled = true,
    whitelistedJobs = { 'police', 'ambulance', 'bcso' },
    ...
}
```

***

## 18. Job chat command

**File:** `resources/[meteostudios]/meteo-chat/shared/config.lua`

Add a new entry to `Config.JobChats.jobs`:

```lua
Config.JobChats = {
    enabled = true,
    jobs = {
        ...
        {
            jobName = 'bcso',
            command = 'bcso',
            label = 'BCSO',
            help = 'Send a message to all BCSO deputies'
        },
    }
}
```

***

## 19. Drug selling / pickpocket blacklists (optional)

**Files:**

* `resources/[meteostudios]/meteo-drugselling/shared/config.lua`
* `resources/[meteostudios]/meteo-pickpocket/shared/config.lua`

`Config.blacklistedJobs` stops these jobs from selling drugs or pickpocketing. Police are not blocked by default (the line is commented out). If you block police, block BCSO the same way:

```lua
Config.blacklistedJobs = {
    'police',
    'bcso',
    'ambulance',
}
```

***

## 20. Vehicle keys (shared keys)

**File:** `resources/[meteostudios]/meteo-vehiclekeys/shared/config.lua`

Add a BCSO block so deputies can share keys for BCSO vehicles:

```lua
Config.sharedKeys = {
    police = { autolock = false, onDutyOnly = true, vehicles = { 'police', 'police2' } },
    bcso = { autolock = false, onDutyOnly = true, vehicles = { 'sheriff', 'sheriff2' } },
    ...
}
```

{% hint style="info" %}
Vehicles handed out by [meteo-jobgarage](../scripts/meteo-jobgarage/) register their own shared keys automatically, so you only need this list for vehicles that come from somewhere else.
{% endhint %}

***

## 21. Inventory police access

**File:** `ox.cfg` (server root)

This convar decides which jobs can search and rob other players' inventories like police. `bcso` and `sasp` are already in it by default - add your job if it uses a different name:

```
setr inventory:police ["police", "bcso", "sasp"]
```

***

## Quick Checklist

After adding the job to `meteo-core/shared/jobs.lua` and restarting, work through this list and update only what applies to your setup:

**In game (F9 > Script Settings)**

* [ ] **Police** > **Access** > **Supported jobs**
* [ ] **Evidence** > **Access** > **Supported jobs**
* [ ] **Police Radar** > **Alerts** > **Allowed jobs**
* [ ] **Jail** > **Sentence** > **Jobs that can jail**
* [ ] **Creator** > **Job Garages** -> garage for `bcso`
* [ ] **Creator** > **Boss Menu** -> boss menu for `bcso`
* [ ] **Creator** > **Appearance** -> job locker for `bcso`
* [ ] **Creator** > **Shops** -> `bcso` in the **Job** column (optional)
* [ ] **Creator** > **Police** -> separate sheriff station (optional)

**In game (MDT)**

* [ ] **Settings - Role Management** -> a role per grade

**Files**

* [ ] `meteo-mdt/shared/config.lua` -> `Config.lab.allowedJobs`
* [ ] `meteo-mdt/shared/config.lua` -> `Config.dispatch` (`defaultJobs`, `calls`, `presets`, `shooting.ignoreJobs`)
* [ ] `meteo-phone/shared/config.lua` -> `Config.services`
* [ ] Crime script dispatch jobs (see the table in step 8)
* [ ] `meteo-radio/shared/config.lua` -> `Config.restrictedChannels`
* [ ] `meteo-cityhall/shared/config.lua` -> `Config.documents.policeBadge.jobs`
* [ ] `meteo-buffs/shared/config.lua` -> `Config.stress.whitelistedJobs`
* [ ] `meteo-chat/shared/config.lua` -> `Config.JobChats.jobs`
* [ ] `meteo-drugselling/shared/config.lua` -> `Config.blacklistedJobs` (optional)
* [ ] `meteo-pickpocket/shared/config.lua` -> `Config.blacklistedJobs` (optional)
* [ ] `meteo-vehiclekeys/shared/config.lua` -> `Config.sharedKeys` entry
* [ ] `ox.cfg` -> `inventory:police`

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a> and our team will help you out.
{% endhint %}
