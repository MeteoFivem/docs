---
description: >-
  Every meteo-mdt export with a simple example and what it gives back -
  permissions, penal codes, licenses, weapons, warrants, BOLOs, reports and more.
icon: code
---

# Exports

Read and write MDT records from your own scripts. All exports are server side.

***

## Permissions

Gate your own script on an MDT permission instead of a raw job check.

### HasPermission(src, key)

```lua
local canView = exports['meteo-mdt']:HasPermission(source, 'view_persons')
print(canView) --> true
```

### GetPlayerRole(src)

The player's MDT role, or `nil` if they have none.

```lua
local role = exports['meteo-mdt']:GetPlayerRole(source)
print(json.encode(role))
--> { "roleId": 4, "roleLabel": "Police Sergeant", "color": "#4A90E2" }
```

### GetEffectivePermissions(src)

Every permission key the player ends up with, after role and dependency resolution.

```lua
local perms = exports['meteo-mdt']:GetEffectivePermissions(source)
print(json.encode(perms))
--> [ "view_persons", "view_person_licenses", "view_licenses", "issue_license" ]
```

***

## Penal Codes

Read-only. Use it to build your own charge, fine or court system without keeping a second copy of the list.

### GetPenalCodes()

Every code.

```lua
local codes = exports['meteo-mdt']:GetPenalCodes()
print(#codes) --> 185
print(json.encode(codes[1]))
```

```lua
-- each code:
{
    id          = 187,
    code        = 'PC-187',
    title       = 'Murder',
    category    = 'Violent',
    class       = 'Felony',          -- Felony | Misdemeanor | Infraction
    description = 'Unlawful killing of a human being.',
    burdens     = { 'Premeditation', 'Use of a deadly weapon' },
    modifiers   = {
        { id = 'm1', label = 'Principal',  descriptor = 'Committed the act', fine = 50000, months = 120 },
        { id = 'm2', label = 'Accomplice', descriptor = 'Aided the act',     fine = 25000, months = 60 },
    },
    hidden   = false,
    internal = false,
}
```

### GetPenalCode(id)

One code by its database id, or `nil`.

```lua
local code = exports['meteo-mdt']:GetPenalCode(42)
print(code.title) --> Speeding (Up to 25 Over)
```

### GetPenalCodeByCode(code)

Same, but by the code string officers actually type.

```lua
local code = exports['meteo-mdt']:GetPenalCodeByCode('PC-187')
print(code.class)               --> Felony
print(code.modifiers[1].fine)   --> 50000
print(code.modifiers[1].months) --> 120
```

### GetPenalCategories()

```lua
local cats = exports['meteo-mdt']:GetPenalCategories()
print(json.encode(cats[1]))
--> { "id": 3, "name": "Violent", "color": "#C0392B" }
```

### GetPenalCodesByCategory(category)

```lua
local traffic = exports['meteo-mdt']:GetPenalCodesByCategory('Traffic')
print(#traffic) --> 23
```

### GetPenalCodesByClass(class)

```lua
local felonies = exports['meteo-mdt']:GetPenalCodesByClass('Felony')
print(#felonies) --> 96
```

### GetPenalCodesByFine(min, max)

Codes with any modifier whose fine falls in the range. Pass `nil` as `max` for no upper bound.

```lua
local pricey = exports['meteo-mdt']:GetPenalCodesByFine(50000, nil)
print(#pricey) --> 7
```

### GetPenalCodesByJailTime(min, max)

Same idea, on jail months.

```lua
local longJail = exports['meteo-mdt']:GetPenalCodesByJailTime(60, nil)
```

### SearchPenalCodes(query)

Matches code, title and description.

```lua
local hits = exports['meteo-mdt']:SearchPenalCodes('assault')
for _, c in ipairs(hits) do print(c.code, c.title) end
--> 5.01  Simple Assault
--> 5.03  Aggravated Assault
--> 5.04  Assault with a Deadly Weapon
```

***

## Licenses

Two layers: license **types** (the definitions) and a person's **issued** licenses. Every type has a stable serial like `LIC-DL-4K2P9`, and that serial is the key every grant export uses. Copy it from the Licenses page in the MDT.

### GetLicenseTypes()

Every type.

```lua
local types = exports['meteo-mdt']:GetLicenseTypes()
print(json.encode(types[1]))
```

```lua
-- each type:
{
    id          = 1,
    name        = "Driver's License",
    identifier  = 'LIC-DL-4K2P9',
    description = 'Standard license to operate road vehicles.',
    image       = '',    -- card image, '' = none
    obtainable  = true,  -- a citizen can buy this one themselves
    price       = 350,
}
```

### GetLicenseType(id)

```lua
local t = exports['meteo-mdt']:GetLicenseType(1)
print(t.name) --> Driver's License
```

### GetLicenseTypeByName(name)

```lua
local t = exports['meteo-mdt']:GetLicenseTypeByName("Driver's License")
print(t.identifier) --> LIC-DL-4K2P9
```

### GetLicenseTypeByIdentifier(serial)

The one you will use most, since the serial is the stable key.

```lua
local t = exports['meteo-mdt']:GetLicenseTypeByIdentifier('LIC-DL-4K2P9')
print(t.price) --> 350
```

### GetObtainableLicenses()

Only the types ticked **Obtainable**, so a counter script needs no license config of its own.

```lua
for _, lt in ipairs(exports['meteo-mdt']:GetObtainableLicenses()) do
    print(lt.name, lt.price)
end
--> Driver's License   350
--> Weapons License    750
```

### IsLicenseObtainable(serial)

```lua
print(exports['meteo-mdt']:IsLicenseObtainable('LIC-DL-4K2P9')) --> true
```

### GetLicenseCardItem()

The inventory item every physical card uses. Read it here instead of hardcoding it.

```lua
local item = exports['meteo-mdt']:GetLicenseCardItem()
print(item) --> meteo_license
```

### CreateLicenseType(data, createdBy?)

`data = { name, description?, identifier?, image?, obtainable?, price? }`. Leave `identifier` out to auto-generate one. `obtainable` defaults to false.

```lua
local rec, err = exports['meteo-mdt']:CreateLicenseType({
    name = 'Pilot License',
    description = 'Authorizes the operation of aircraft.',
    obtainable = true,
    price = 1200,
}, 'DMV System')

print(rec.identifier) --> LIC-PL-3R6W7
```

Errors: `name_required`, `duplicate_name`, `duplicate_identifier`, `invalid_image`.

### GiveLicense(citizenid, serial, issuedBy?)

Issues a license. One active license per type per person.

```lua
local ok, err, id = exports['meteo-mdt']:GiveLicense('ABC12345', 'LIC-DL-4K2P9', 'DMV Test')
print(ok, err, id) --> true  nil  51
```

Errors: `already_active`, `unknown_type`, `person_not_found`.

### HasLicense(citizenid, serial)

```lua
local status = exports['meteo-mdt']:HasLicense('ABC12345', 'LIC-DL-4K2P9')
print(status) --> VALID
```

Returns `'VALID'`, `'SUSPENDED'`, or `nil` if they hold none. Check `== 'VALID'` for "valid right now".

### SuspendLicense(citizenid, serial, reason?, by?)

VALID to SUSPENDED.

```lua
local ok, err = exports['meteo-mdt']:SuspendLicense('ABC12345', 'LIC-DL-4K2P9', 'Reckless driving', 'Officer Vargas')
print(ok) --> true
```

Error: `no_valid_license`.

### ReinstateLicense(citizenid, serial, by?)

SUSPENDED back to VALID.

```lua
local ok, err = exports['meteo-mdt']:ReinstateLicense('ABC12345', 'LIC-DL-4K2P9', 'Officer Vargas')
```

Error: `no_suspended_license`.

### RevokeLicense(citizenid, serial, reason?, by?)

Terminal, cannot be reinstated.

```lua
local ok, err = exports['meteo-mdt']:RevokeLicense('ABC12345', 'LIC-DL-4K2P9', 'Multiple DUIs', 'Officer Knight')
```

Error: `no_active_license`.

### GetPlayerLicenses(citizenid)

Every license they hold, active first.

```lua
for _, l in ipairs(exports['meteo-mdt']:GetPlayerLicenses('ABC12345')) do
    print(l.type, l.status)
end
--> Driver's License   VALID
--> Weapons License    SUSPENDED
```

```lua
-- each record:
{
    id         = 51,
    type       = "Driver's License",
    identifier = 'LIC-DL-4K2P9',
    status     = 'VALID',        -- VALID | SUSPENDED | REVOKED | UNAVAILABLE
    reason     = '',
    issuedBy   = 'DMV Test',
    issuedAt   = 1782364949000,  -- epoch ms
    updatedBy  = 'DMV Test',
    updatedAt  = 1782364949000,
}
```

`UNAVAILABLE` means the license type was deleted.

### GiveLicenseItem(source, serial)

Hands an **online** player the physical card. Takes a server id, not a citizenid. They must already hold the license.

```lua
local ok, err = exports['meteo-mdt']:GiveLicenseItem(source, 'LIC-DL-4K2P9')
print(ok, err) --> true  nil
```

Errors: `no_player`, `unknown_type`, `no_license`, `inv_full`.

Using the card shows it to nearby players. Status is re-read live on every use, so a card printed before a revoke still shows as revoked.

### HasLicenseItem(source, serial)

Do they already carry the printed card? Check before offering a reprint.

```lua
if not exports['meteo-mdt']:HasLicenseItem(source, 'LIC-DL-4K2P9') then
    -- charge a reprint fee, then GiveLicenseItem
end
```

### Full example: a license counter

No per-license config anywhere in the calling script.

```lua
local function sellLicense(src, serial)
    local player = exports.qbx_core:GetPlayer(src)
    if not player then return end
    local cid = player.PlayerData.citizenid

    local lt = exports['meteo-mdt']:GetLicenseTypeByIdentifier(serial)
    if not lt or not lt.obtainable then return end

    -- already hold it? then this is just a replacement card
    local held = exports['meteo-mdt']:HasLicense(cid, serial)
    if held and exports['meteo-mdt']:HasLicenseItem(src, serial) then return end

    -- check inventory room BEFORE taking money
    local item = exports['meteo-mdt']:GetLicenseCardItem()
    if not exports.ox_inventory:CanCarryItem(src, item, 1) then return end

    local price = held and REPRINT_FEE or lt.price
    if not player.Functions.RemoveMoney('cash', price, 'license') then return end

    if not held then
        exports['meteo-mdt']:GiveLicense(cid, serial, 'City Hall')
    end
    exports['meteo-mdt']:GiveLicenseItem(src, serial)
end
```

***

## Weapons

A registry keyed by the ox_inventory weapon **serial**. The item lives in ox_inventory; this is the provenance layer.

### RegisterWeapon(data)

`data = { serial, weapon, owner = citizenid, ownerName?, source?, components?, by? }`.

```lua
local rec, err = exports['meteo-mdt']:RegisterWeapon({
    serial     = weaponMetadata.serial,   -- the ox_inventory metadata.serial
    weapon     = 'WEAPON_PISTOL',
    owner      = buyerCitizenid,
    source     = 'armory',
    components = weaponMetadata.components,
    by         = 'LSPD Armory',
})

print(rec.label) --> Pistol
```

Errors: `serial_required`, `weapon_required`, `owner_required`, `owner_not_found`, `already_registered`.

### GetWeapon(serial)

```lua
local w = exports['meteo-mdt']:GetWeapon('734182ABC901556')
print(w.label, w.owner.name, w.stolen.active)
--> Pistol   John Doe   false
```

```lua
-- each record:
{
    serial       = '734182ABC901556',
    weapon       = 'WEAPON_PISTOL',
    label        = 'Pistol',
    owner        = { citizenid = 'ABC12345', name = 'John Doe' }, -- or nil
    source       = 'manual',   -- manual | armory | ...
    components   = { 'Flashlight', 'Extended Clip' },
    registeredBy = 'M. Vargas',
    registeredAt = 1782300000000,  -- epoch ms
    gone         = false,          -- true = unregistered, kept on record
    stolen       = { active = false, reason = nil, by = nil, at = nil },
    seized       = { active = false, reason = nil, by = nil, at = nil },
    bolo         = { active = false, count = 0, items = {} },
}
```

### IsWeaponRegistered(serial)

```lua
print(exports['meteo-mdt']:IsWeaponRegistered(serial)) --> false
```

### GetPlayerWeapons(citizenid)

Newest first.

```lua
for _, w in ipairs(exports['meteo-mdt']:GetPlayerWeapons('ABC12345')) do
    print(w.label, w.serial, w.stolen.active)
end
--> Pistol           734182ABC901556   false
--> Carbine Rifle    99120XYZ778341    true
```

### ChangeWeaponOwner(serial, citizenid, by?)

```lua
local ok, err = exports['meteo-mdt']:ChangeWeaponOwner(serial, 'QWE45612', 'DOJ Transfer')
print(ok) --> true
```

Errors: `not_registered`, `owner_not_found`.

### UnregisterWeapon(serial, by?)

Soft delete. Keeps the profile and history, marks it gone.

```lua
local ok = exports['meteo-mdt']:UnregisterWeapon(serial, 'Armory Buyback')
```

### GetWeaponHistory(serial)

Newest first.

```lua
for _, e in ipairs(exports['meteo-mdt']:GetWeaponHistory(serial)) do
    print(e.event, e.detail)
end
--> stolen_flagged   Reported taken in a burglary
--> owner_changed    To John Doe
--> registered       LSPD Armory
```

Events: `registered`, `owner_changed`, `unregistered`, `stolen_flagged`, `stolen_cleared`, `seized_flagged`, `seized_cleared`.

### GetWeaponBolos(serial)

```lua
local b = exports['meteo-mdt']:GetWeaponBolos(serial)
print(b.active, b.count) --> true  1
print(b.items[1].title)  --> Pistol used in Vinewood shooting
```

***

## Wanted, BOLOs and Stolen Vehicles

### GetWantedList()

Every wanted subject, newest first, with a resolved label.

```lua
for _, w in ipairs(exports['meteo-mdt']:GetWantedList()) do
    print(w.subjectType, w.subjectId, w.label, w.reason)
end
--> person    ABC12345   John Doe   Failed to appear
--> vehicle   8XYZ123    Kuruma     Fled a pursuit
```

### IsWanted(subjectType, subjectId)

`subjectType` is `person` or `vehicle`.

```lua
local w = exports['meteo-mdt']:IsWanted('person', 'ABC12345')
print(json.encode(w))
--> { "active": true, "reason": "Failed to appear", "by": "M. Vargas", "at": 1782300000 }
--> { "active": false }   when not wanted
```

### SetWanted(subjectType, subjectId, reason?, by?)

Re-flagging just updates the reason. Notifies the person if they are online.

```lua
exports['meteo-mdt']:SetWanted('person', 'ABC12345', 'Armed robbery - RPT-118', 'DOJ System')
exports['meteo-mdt']:SetWanted('vehicle', '8XYZ123', 'Fled a pursuit', 'Dispatch')
```

Errors: `bad_subject_type`, `bad_subject_id`.

### ClearWanted(subjectType, subjectId, by?)

No-op if they were not wanted.

```lua
local ok, err = exports['meteo-mdt']:ClearWanted('person', 'ABC12345', 'DOJ System')
```

### GetStolenVehicles()

```lua
for _, s in ipairs(exports['meteo-mdt']:GetStolenVehicles()) do
    print(s.plate, s.reason, s.by)
end
--> 8XYZ123   Taken from Legion Sq   M. Vargas
```

### GetBolos() / GetActiveBolos() / GetBolo(id)

`GetActiveBolos` is the cheap one to poll. `GetBolos` returns the full history, which keeps growing as BOLOs are resolved.

```lua
local active = exports['meteo-mdt']:GetActiveBolos()
local one    = exports['meteo-mdt']:GetBolo(3)

print(#active)      --> 4
print(one.priority) --> high
```

```lua
-- each record:
{
    id          = 3,
    subjectType = 'vehicle',   -- person | vehicle | property | other
    subjectId   = '8XYZ123',   -- nil for 'other'
    title       = 'Black Kuruma, tinted windows',
    details     = 'Fled north on Route 68...',
    priority    = 'high',      -- high | medium | low
    status      = 'active',    -- active | resolved
    createdBy   = 'M. Vargas',
    createdAt   = 1782360000000,
    updatedBy   = 'M. Vargas',
    updatedAt   = 1782360000000,
}
```

### CreateBolo(data, createdBy?)

`subjectType` defaults to `other`, `priority` to `medium`.

```lua
local rec, err = exports['meteo-mdt']:CreateBolo({
    subjectType = 'vehicle',
    subjectId   = '8XYZ123',
    title       = 'Black Kuruma, tinted windows',
    details     = 'Fled a traffic stop northbound on Route 68.',
    priority    = 'high',
}, 'Dispatch')

print(rec.id) --> 3
```

Errors: `invalid_data`, `title_required`.

### SetBoloStatus(id, status, by?)

`status` is `resolved` or `active`.

```lua
local ok, err = exports['meteo-mdt']:SetBoloStatus(3, 'resolved', 'Dispatch')
```

Error: `not_found`.

### Live updates instead of polling

`meteo-mdt:server:vehicleAlertsChanged` fires whenever a BOLO, wanted flag or stolen flag changes. No payload, so re-pull what you need.

```lua
AddEventHandler('meteo-mdt:server:vehicleAlertsChanged', function()
    -- rebuild your cached plate set
end)
```

***

## Warrants

Subject can be a `person` (citizenid), `vehicle` (plate), `phone` (number), `property` (id) or `other`.

### GetWarrants() / GetActiveWarrants() / GetWarrant(id)

```lua
local all    = exports['meteo-mdt']:GetWarrants()        -- all, active first
local active = exports['meteo-mdt']:GetActiveWarrants()  -- active only
local one    = exports['meteo-mdt']:GetWarrant(12)       -- one or nil

print(one.title)  --> Armed robbery - RPT-118
print(one.status) --> active
```

```lua
-- each record:
{
    id           = 12,
    subjectType  = 'person',      -- person | vehicle | phone | property | other
    subjectId    = 'ABC12345',
    subjectLabel = 'John Doe',    -- snapshot of the name / model / address
    warrantType  = 'arrest',      -- arrest | search
    title        = 'Armed robbery - RPT-118',
    reason       = 'Failure to appear...',
    priority     = 'high',        -- high | medium | low
    status       = 'active',      -- active | served | recalled | expired
    judge        = 'Judge Harmon',
    expiresAt    = 1785000000000, -- epoch ms, or nil
    createdBy    = 'M. Vargas',
    createdAt    = 1782360000000,
    updatedBy    = 'M. Vargas',
    updatedAt    = 1782360000000,
}
```

### GetWarrantsForSubject(subjectType, subjectId)

Active warrants naming one subject. The "does this person have a warrant" call.

```lua
local hits = exports['meteo-mdt']:GetWarrantsForSubject('person', 'ABC12345')
print(#hits) --> 1
```

### CreateWarrant(data, createdBy?)

`subjectType` defaults to `person`, `warrantType` to `arrest`, `priority` to `medium`. Anything except an `other` warrant needs a `subjectId`.

```lua
local rec, err = exports['meteo-mdt']:CreateWarrant({
    subjectType = 'person',
    subjectId   = 'ABC12345',
    warrantType = 'arrest',
    title       = 'Armed robbery - RPT-118',
    reason      = 'Failure to appear; probable cause from RPT-118.',
    priority    = 'high',
    judge       = 'Judge Harmon',
}, 'DOJ System')

print(rec.id) --> 12
```

Errors: `title_required`, `subject_required`.

### SetWarrantStatus(id, status, by?)

`status` is `active`, `served`, `recalled` or `expired`.

```lua
local ok, err = exports['meteo-mdt']:SetWarrantStatus(12, 'served', 'Officer Vargas')
```

Error: `not_found`.

***

## Reports

### GetReports() / GetReport(id)

```lua
local all = exports['meteo-mdt']:GetReports()   -- newest first
local one = exports['meteo-mdt']:GetReport(42)  -- one or nil

print(one.number) --> RPT-42
print(one.status) --> OPEN
```

```lua
-- each record:
{
    id           = '42',          -- string
    number       = 'RPT-42',      -- prefix depends on type
    title        = 'Store robbery on Vespucci',
    type         = 'Incident',
    status       = 'OPEN',        -- OPEN | CLOSED | COLD
    incidentDate = '2026-06-28',
    location     = 'Vespucci Blvd',
    description  = '',
    createdBy    = 'Officer Vargas',
    createdAt    = 1751130000000, -- epoch ms
    -- officers, suspects, vehicles, weapons, photos etc come back empty here
    -- and are filled in from inside the MDT
}
```

### CreateReport(type?, createdBy?)

Opens a blank report. Types are `Incident`, `Investigative`, `Master File`, `FTO` and `Disciplinary`, each with its own number prefix and permissions.

```lua
local report = exports['meteo-mdt']:CreateReport('Incident', 'Dispatch')
print(report.number) --> RPT-43
```

### SetReportStatus(id, status, by?)

```lua
local ok, err = exports['meteo-mdt']:SetReportStatus(42, 'CLOSED', 'Judge Miller')
print(ok) --> true
```

Error: `not_found`.

***

## Vehicles

### AddVehicleHistory(plate, event, detail?, actorName?)

Adds one event to the History panel on the MDT vehicle profile.

```lua
local ok, err = exports['meteo-mdt']:AddVehicleHistory(
    'ABC 123', 'impounded', 'Left on a fire hydrant', 'Officer Vargas'
)
print(ok) --> true
```

Allowed events: `impounded`, `depot`, `released`, `stored`, `retrieved`, `transferred`. Anything else is refused, since the UI has no label for it.

The plate is trimmed for you and must already be known to the server, so a typo cannot create an orphan timeline.

Errors: `invalid_data`, `invalid_plate`, `unknown_event`, `unknown_vehicle`.

***

## Prescriptions

For a pharmacy or hospital script.

### GetPrescriptions(citizenid)

Active first, then expired, then cancelled. Each carries its **effective** status, so you never do date maths.

```lua
for _, p in ipairs(exports['meteo-mdt']:GetPrescriptions('ABC12345')) do
    print(p.rx, p.medication, p.status)
end
--> RX-0014   Ibuprofen    ACTIVE
--> RX-0009   Amoxicillin  EXPIRED
```

```lua
-- each record:
{
    id         = 14,
    rx         = 'RX-0014',
    citizenid  = 'ABC12345',
    patient    = 'John Doe',
    medication = 'Ibuprofen',
    dosage     = '200mg',
    frequency  = 'Twice daily',
    notes      = '',
    status     = 'ACTIVE',      -- ACTIVE | EXPIRED | CANCELLED
    expiresOn  = '2026-09-01',  -- nil if it never expires
    issuedBy   = 'Dr. Vargas',
    issuedAt   = 1751130000000, -- epoch ms
}
```

### HasActivePrescription(citizenid, medication?)

True only while a prescription is valid right now. Omit `medication` to ask "any active script at all".

```lua
print(exports['meteo-mdt']:HasActivePrescription('ABC12345', 'Ibuprofen')) --> true
```

### AddPrescription(data)

`data = { citizenid, medication, dosage?, frequency?, notes?, expiresOn?, issuedBy? }`. `issuedBy` defaults to `System`.

```lua
local ok, err, id = exports['meteo-mdt']:AddPrescription({
    citizenid  = 'ABC12345',
    medication = 'Ibuprofen',
    dosage     = '200mg',
    frequency  = 'Twice daily',
    expiresOn  = '2026-09-01',
    issuedBy   = 'Dr. Vargas',
})
print(ok, err, id) --> true  nil  14
```

Errors: `invalid_data`, `invalid_citizenid`, `medication_required`, `person_not_found`.

The patient gets a notification and the MDT profile refreshes on its own.

***

## Lab and Forensics

### GetFingerprint(citizenid)

The on-file print, or `nil` if forensics never collected one.

```lua
local fp = exports['meteo-mdt']:GetFingerprint('ABC12345')
print(fp.collectedBy, fp.lab) --> Officer Vargas   Mission Row
```

```lua
-- record:
{
    citizenid   = 'ABC12345',
    fingerprint = 'A7F3-9C21-...',
    collectedBy = 'Officer Vargas',
    collectedAt = 1751130000000, -- epoch ms
    lab         = 'Mission Row',
}
```

### IsFingerprintCollected(citizenid)

```lua
print(exports['meteo-mdt']:IsFingerprintCollected('ABC12345')) --> false
-- nothing on file, send them to booking
```

### GetLabOrder(code)

```lua
local order = exports['meteo-mdt']:GetLabOrder('LAB-0042')
print(order.label, order.status) --> Blood sample   processing
```

```lua
-- record:
{
    id              = 42,
    code            = 'LAB-0042',
    label           = 'Blood sample',
    status          = 'processing',
    ownerCid        = 'ABC12345',
    ownerName       = 'John Doe',
    bench           = 'dna',
    processedByName = 'Tech Rivera',
    processEndsAt   = 1751130000000, -- epoch ms, nil if not processing
}
```

### GetLabReportsForCitizen(citizenid)

Every filed lab report that implicated this citizen.

```lua
for _, r in ipairs(exports['meteo-mdt']:GetLabReportsForCitizen('ABC12345')) do
    print(r.code, r.label)
end
--> LAB-0042   Blood sample
```

***

## Photos

### AddPhoto(data)

`data = { url, name?, category?, addedBy?, citizenid?, coords? }`. URLs are checked against the allowlist in `Config.ImageValidation`. Unknown categories fall back to "Other". Pass `citizenid` to also attach it to that person's profile.

```lua
local id, err = exports['meteo-mdt']:AddPhoto({
    url       = 'https://i.imgur.com/abc123.png',
    name      = 'Booking photo',
    category  = 'Mugshots',
    addedBy   = 'Booking System',
    citizenid = 'ABC12345',
})
print(id, err) --> 102  nil
-- on failure: nil  host_not_allowed
```

### GetPhotoCategories()

```lua
local cats = exports['meteo-mdt']:GetPhotoCategories()
print(json.encode(cats[1]))
--> { "id": 2, "name": "Mugshots", "color": "#4A90E2" }
```

### GetPhotosByCategory(category, limit?)

Newest first. `limit` defaults to 100 and caps at 500.

```lua
local shots = exports['meteo-mdt']:GetPhotosByCategory('Mugshots', 50)
print(#shots) --> 12
```

```lua
-- each photo:
{
    id         = 102,
    url        = 'https://i.imgur.com/abc123.png',
    name       = 'Booking photo',
    category   = 'Mugshots',
    addedBy    = 'Booking System',      -- falls back to '-'
    addedByCid = 'ABC12345',            -- nil if not set
    createdAt  = '2026-06-28 14:22:29', -- SQL datetime string
    coords     = { x = 215.3, y = -810.1, z = 30.7 }, -- nil if no location
}
```

### GetPersonPrimaryPhoto(citizenid)

Their MDT display image, or `nil`. Same source the profile header uses, so another resource can show a matching avatar.

```lua
local url = exports['meteo-mdt']:GetPersonPrimaryPhoto('ABC12345')
print(url) --> https://i.imgur.com/abc123.png
```

***

## Items

For a police armory or supply shelf.

### GiveTicketBook(source, pages?)

`pages` defaults to the configured pages per book.

```lua
local ok, err = exports['meteo-mdt']:GiveTicketBook(source, 25)
print(ok, err) --> true  nil
```

Errors: `no_player`, `inv_full`.

### GetTicketBookPages(source)

Pages left across every book they carry, so you only offer a refill when needed.

```lua
local left = exports['meteo-mdt']:GetTicketBookPages(source)
print(left) --> 3

if left < 5 then
    exports['meteo-mdt']:GiveTicketBook(source)
end
```

### GiveFormPad(source, sheets?)

```lua
local ok, err = exports['meteo-mdt']:GiveFormPad(source)
```

Errors: `no_player`, `inv_full`.

***

## Activity Logs

### AddActivityLog(data)

Pushes an entry onto a citizen's roster profile under **Activity Logs**, and onto the global Activity Logs page.

`data = { src | citizenid, actorName?, category, action, description, meta? }`.

```lua
local ok = exports['meteo-mdt']:AddActivityLog({
    src         = source,               -- resolves their name + citizenid
    category    = 'armory',             -- groups entries, becomes a filter chip
    action      = 'weapon_checkout',    -- picks the row icon
    description = 'Checked out 1x Carbine Rifle',
    meta        = { serial = 'XYZ123', armory = 'Mission Row' },
})
print(ok) --> true
```

- `src` **or** `citizenid` is required. Use `citizenid` plus `actorName` for a system actor.
- `category` and `action` are lowercase keys (`[a-z0-9_]`), max 32 and 48 chars.
- `description` is the full sentence shown in the log, max 255 chars.
- `meta` is any JSON-able table, max 2048 chars encoded.

Returns `false` if a required field is missing, activity logs are off in config, or the write queue is full.
