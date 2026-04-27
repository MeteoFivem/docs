---
description: >-
  Add a new LEO-type job (BCSO, Sheriff, State Police, etc.) to the meteo
  server.
icon: shield-halved
---

# How to Add a LEO Job

This guide lists every config you need to touch when adding a new LEO-type job (e.g. BCSO, Sheriff, State Police). Replace `bcso` in the examples with your new job name.

***

## 1. Define the job

**File:** `resources/[meteostudios]/meteo-core/shared/jobs.lua`

Add a new entry alongside `police`. The `type = 'leo'` field is what makes our scripts treat it as law-enforcement.

```lua
bcso = {
    label = 'Blaine County Sheriff',
    type = 'leo',
    defaultDuty = true,
    offDutyPay = false,
    icon = 'local_police',
    showInPhone = true,
    grades = {
        ['0'] = { name = 'Cadet', payment = 50 },
        ['1'] = { name = 'Deputy', payment = 75 },
        ['2'] = { name = 'Sergeant', payment = 100 },
        ['3'] = { name = 'Lieutenant', payment = 125 },
        ['4'] = { name = 'Sheriff', isboss = true, payment = 150 },
    },
},
```

After this, anything that already checks `job.type == 'leo'` works automatically (cop counts, evidence/fingerprint server validation, dispatch alerts, etc.). You only need the configs below to expose targets, blips, vehicles, and access.

***

## 2. Police station targets (duty toggle, stash, trash, cameras, armory)

**File:** `resources/[meteostudios]/meteo-policejob/shared/config.lua`

Add the job name to `Config.leoJobs`:

```lua
Config.leoJobs = { 'police', 'bcso' }
```

***

## 3. Fingerprint scanner targets

**File:** `resources/[meteostudios]/meteo-fingerscanner/shared/config.lua`

```lua
Config.leoJobs = { 'police', 'bcso' }
```

***

## 4. Evidence stash and analyze targets

**File:** `resources/[meteostudios]/meteo-evidence/shared/config.lua`

```lua
Config.leoJobs = { 'police', 'bcso' }
```

***

## 5. MDT access

**File:** `resources/[meteostudios]/meteo-mdt/shared/config.lua`

Add to the allowed-jobs list (line ~51):

```lua
Config.allowedJobs = {
    'police',
    'bcso',
}
```

`Config.account = 'police'` (line ~87) is the society bank account name. Leave it as `'police'` if BCSO shares the same treasury, or change it if BCSO has its own society account.

***

## 6. Dispatch (911 alerts received)

**File:** `resources/[meteostudios]/meteo-dispatch/shared/config.lua`

Add to the receiver job list (line ~29):

```lua
Config.policeJobs = {
    'police',
    'bcso',
}
```

***

## 7. Police radar

**File:** `resources/[meteostudios]/meteo-policeradar/shared/config.lua`

Add to the allowed-jobs list (line ~66):

```lua
Config.allowedJobs = {
    'police',
    'bcso',
}
```

***

## 8. Job radio channels

**File:** `resources/[meteostudios]/meteo-radio/shared/config.lua`

If BCSO should share a fixed channel, add the job name to that channel's job list:

```lua
Config.jobChannels = {
    [1] = { 'police', 'bcso' },
}
```

***

## 9. Job garage (vehicles)

**File:** `resources/[meteostudios]/meteo-jobgarage/shared/config.lua`

Each garage entry has a `job = "police"` field. Either duplicate the police garage entries with `job = "bcso"`, or change them to support both. Affected entries are around lines 34, 251, 642, 692.

***

## 10. Boss menu (society management)

**File:** `resources/[meteostudios]/meteo-bossmenuv2/shared/config.lua`

Add a new job entry around line 34:

```lua
Config.jobs = {
    ['police'] = { ... },
    ['bcso'] = {
        -- copy police block, change coords/society name as needed
    },
}
```

***

## 11. Buffs (stress whitelist)

**File:** `resources/[meteostudios]/meteo-buffs/shared/config.lua`

If LEOs should be exempt from stress, add to `whitelistedJobs` (line ~40):

```lua
whitelistedJobs = { 'police', 'ambulance', 'bcso' },
```

***

## 12. Job chat command

**File:** `resources/[meteostudios]/meteo-chatv2/shared/config.lua`

Add a new entry in `Config.jobChats` (around line ~51):

```lua
{
    jobName = 'bcso',
    command = 'bcso',
    -- copy other police fields
},
```

***

## 13. Properties (apartment/house access)

**File:** `resources/[meteostudios]/meteo-properties/shared/config.lua`

If BCSO should access police-only buildings, add to the relevant `jobs` tables (lines ~142, ~292):

```lua
['police'] = 3,
['bcso'] = 3,
```

***

## 14. Apartments (police access doors, etc.)

**File:** `resources/[meteostudios]/meteo-apartments/shared/config.lua`

Same idea as properties (lines ~201, ~282):

```lua
['police'] = 0,
['bcso'] = 0,
```

***

## 15. Appearance (uniforms / outfit access)

**File:** `resources/[meteostudios]/meteo-appearance/shared/config.lua`

Each restricted outfit has `job = 'police'`. Either duplicate the entry for `bcso` or change to allow both (lines ~94, ~99).

***

## 16. Shops (job-restricted items)

**File:** `resources/[meteostudios]/meteo-shops/shared/config.lua`

If BCSO should buy police-restricted items, add the job to `requiredJob` (line ~228):

```lua
requiredJob = { 'mechanic', 'police', 'bcso' },
```

***

## 17. City Hall (police badge purchase)

**File:** `resources/[meteostudios]/meteo-cityhallv2/shared/config.lua`

The police badge document at line ~78 uses `jobs = { 'police' }` (job-name based by design). Add BCSO if they should also be able to buy it:

```lua
jobs = { 'police', 'bcso' },
```

***

## 18. Jail (jail/unjail permission)

**File:** `resources/[meteostudios]/meteo-jail/shared/config.lua`

Strict job-name allowlist. Add BCSO explicitly (line ~34):

```lua
Config.allowedJobs = {
    ['police'] = true,
    ['bcso'] = true,
}
```

***

## 19. Boosting / drug selling / pickpocket blacklists

**Files:**

* `resources/[meteostudios]/meteo-boosting/shared/config.lua` (line ~81)
* `resources/[meteostudios]/meteo-drugselling/shared/config.lua` (line ~39)
* `resources/[meteostudios]/meteo-pickpocket/shared/config.lua` (line ~40)

These are blacklists - players with these jobs cannot do the criminal activity. Add BCSO if you want them blocked too:

```lua
blacklistedJobs = {
    'police',
    'bcso',
}
```

Note: cop-count checks in these scripts already use `job.type == 'leo'`, so BCSO automatically counts toward "required cops" the moment the job is defined.

***

## 20. Vehicle keys (qbx\_vehiclekeys shared keys)

**File:** `resources/[meteostudios]/qbx_vehiclekeys/config/client.lua`

Around line ~69. Duplicate the `police` block for BCSO so deputies can share keys for BCSO vehicles:

```lua
sharedKeys = {
    police = { ... },
    bcso = {
        enableAutolock = true,
        requireOnduty = true,
        classes = {},
        vehicles = {
            [`sheriff`] = true,
            [`sheriff2`] = true,
        },
    },
}
```

***

## Quick Checklist

After adding the job to `meteo-core/shared/jobs.lua`, work through this list and update only the configs that apply to your setup:

* [ ] `meteo-policejob/shared/config.lua` -> `Config.leoJobs`
* [ ] `meteo-fingerscanner/shared/config.lua` -> `Config.leoJobs`
* [ ] `meteo-evidence/shared/config.lua` -> `Config.leoJobs`
* [ ] `meteo-mdt/shared/config.lua` -> allowed jobs
* [ ] `meteo-dispatch/shared/config.lua` -> receiver jobs
* [ ] `meteo-policeradar/shared/config.lua` -> allowed jobs
* [ ] `meteo-radio/shared/config.lua` -> job channels
* [ ] `meteo-jobgarage/shared/config.lua` -> garage entries
* [ ] `meteo-bossmenuv2/shared/config.lua` -> society entry
* [ ] `meteo-buffs/shared/config.lua` -> stress whitelist
* [ ] `meteo-chatv2/shared/config.lua` -> chat command
* [ ] `meteo-properties/shared/config.lua` -> access lists
* [ ] `meteo-apartments/shared/config.lua` -> access lists
* [ ] `meteo-appearance/shared/config.lua` -> outfit access
* [ ] `meteo-shops/shared/config.lua` -> required jobs
* [ ] `meteo-cityhallv2/shared/config.lua` -> police badge jobs
* [ ] `meteo-jail/shared/config.lua` -> allowed jobs
* [ ] `meteo-boosting/shared/config.lua` -> blacklist (optional)
* [ ] `meteo-drugselling/shared/config.lua` -> blacklist (optional)
* [ ] `meteo-pickpocket/shared/config.lua` -> blacklist (optional)
* [ ] `[meteostudios]/qbx_vehiclekeys/config/client.lua` -> sharedKeys entry

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a> and our team will help you out.
{% endhint %}
