---
description: >-
  Use meteo-mdt exports to read and write MDT records from your own scripts -
  permissions, penal codes, licenses, weapons, warrants, BOLOs and photos.
icon: code
---

# Exports

The MDT is the record system for the whole server, so other scripts can read from it and write to it instead of keeping their own copies. A city hall counter asks the MDT what licenses are on sale, a police armory registers the weapon it just handed out, a robbery script flags a plate wanted.

{% hint style="info" %}
All of these are **server to server**. Call them from your own server scripts. They are trusted, so they do not run a player permission check - you decide who is allowed to reach them.
{% endhint %}

```lua
exports['meteo-mdt']:ExportName(args)
```

***

## What You Get

| Area | Exports | What it is for |
| ---- | ------- | -------------- |
| Permissions | `HasPermission`, `GetPlayerRole`, `GetEffectivePermissions` | Gate your own script on an MDT permission instead of a raw job check |
| Penal codes | `GetPenalCodes`, `GetPenalCode`, `GetPenalCodesByCategory`, `GetPenalCodesByClass`, `GetPenalCodesByFine`, `GetPenalCodesByJailTime`, `SearchPenalCodes`, `GetPenalCategories` | Read the charge list for your own charge or fine system |
| Licenses | `GetLicenseTypes`, `GetLicenseTypeByIdentifier`, `GetObtainableLicenses`, `IsLicenseObtainable`, `GetPlayerLicenses`, `HasLicense`, `GiveLicense`, `SuspendLicense`, `ReinstateLicense`, `RevokeLicense`, `GiveLicenseItem`, `HasLicenseItem`, `GetLicenseCardItem`, `CreateLicenseType` | Sell licenses at a counter, check one, or grant and revoke from a script |
| Weapons | `RegisterWeapon`, `IsWeaponRegistered`, `GetWeapon`, `GetPlayerWeapons`, `GetWeaponHistory`, `GetWeaponBolos`, `ChangeWeaponOwner`, `UnregisterWeapon` | Register weapons from an armory or gun shop and look them up by serial |
| Wanted and BOLO | `SetWanted`, `ClearWanted`, `IsWanted`, `GetWantedList`, `CreateBolo`, `SetBoloStatus`, `GetBolos`, `GetStolenVehicles` | Flag a person or vehicle wanted, post a BOLO, read the wanted list |
| Warrants | `CreateWarrant`, `SetWarrantStatus` | Issue arrest and search warrants against a person, vehicle, phone or property |
| Photos | `AddPhoto`, `GetPhotosByCategory`, `GetPhotoCategories` | Push mugshots or scene photos into the photo reel |
| Activity logs | `AddActivityLog` | Push per citizen activity that shows on roster member profiles |

Reads come from an in-memory cache where possible, so they cost nothing extra. Writes are audit logged, and most take an optional `by` argument to name the caller.

***

## Examples

### Gate a menu on an MDT permission

```lua
if exports['meteo-mdt']:HasPermission(source, 'view_persons') then
    -- open the records menu
end
```

### Sell a license at a counter

The counter needs no license config of its own. Add a license in the MDT, tick **Obtainable**, and it shows up here with its name, description, image and price.

```lua
local menu = exports['meteo-mdt']:GetObtainableLicenses()

local function sellLicense(src, serial)
    local player = exports['meteo-core']:GetPlayer(src)
    if not player then return end

    local licenseType = exports['meteo-mdt']:GetLicenseTypeByIdentifier(serial)
    if not licenseType or not licenseType.obtainable then return end

    local item = exports['meteo-mdt']:GetLicenseCardItem()
    if not exports.ox_inventory:CanCarryItem(src, item, 1) then return end

    if not player.Functions.RemoveMoney('cash', licenseType.price, 'license') then return end

    exports['meteo-mdt']:GiveLicense(player.PlayerData.citizenid, serial, 'City Hall')
    exports['meteo-mdt']:GiveLicenseItem(src, serial)
end
```

### Register a weapon from an armory

```lua
exports['meteo-mdt']:RegisterWeapon({
    serial = serial,
    citizenid = player.PlayerData.citizenid,
    weapon = 'WEAPON_PISTOL',
    source = 'armory',
    registeredBy = officerName,
})
```

### Flag a stolen vehicle

```lua
exports['meteo-mdt']:SetWanted('vehicle', plate, 'Reported stolen from Vinewood', 'Dispatch')
```

***

{% hint style="success" %}
Every export is documented in full inside the script itself under `meteo-mdt/docs/exports/`, with the exact record shapes each one returns. Open a ticket on our Discord if you want help wiring your own script into it.
{% endhint %}
