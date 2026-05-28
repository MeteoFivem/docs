---
description: Changelogs for the meteo dealerships script.
icon: clock-rotate-left
---

# Changelogs

All updates, new features, fixes and improvements to the meteo dealerships script.

{% hint style="success" %}
**Need help with an update or have a question?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}

***

### 1.3.0

#### Changes

* Added client based vehicle spawning support for larger servers. `Config.spawnMode`
* Fixed major issues with financing ui side and payment side.
* Added new meteo phone app integration hooks for finance data. 
* Meteo phone finance app - https://github.com/MeteoStudios/meteo-customapp-finance

#### Modified Files

* `web\*`
* `fxmanifest.lua`
* `client\*`
* `CHANGELOG.md`
* `server\*`
* `shared\config.lua`
* `shared\rename.lua`

***

### 1.2.0

#### Changes

* Added per-dealership financing toggle (`finance.enabled`)
* Fixed activity logs failing on databases with mixed table collations
* Fixed finance request silently charging full price when financing is disabled

#### Modified Files

* `fxmanifest.lua`
* `server\sv_functions.lua`
* `server\sv_shop.lua`
* `shared\config.lua`

***

### 1.1.0

#### Changes

* Added job applications support with application ped per owned dealership
* Added tablet holding animation when dealer admin UI is open
* Added logs support with ox_lib logger and Discord webhook
* Added new translations
* Added nui_callback_strict_mode to fxmanifest
* Updated vehicle classes to be read from config instead of hardcoded
* Updated UI with various tweaks

#### Modified Files

* `fxmanifest.lua`
* `server\*`
* `client\*`
* `web\*`
* `shared\config.lua`
* `locales\*`
