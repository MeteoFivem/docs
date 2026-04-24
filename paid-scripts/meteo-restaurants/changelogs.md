---
description: Changelogs for the meteo restaurants script.
icon: clock-rotate-left
---

# Changelogs

All updates, new features, fixes and improvements to the meteo restaurants script.

{% hint style="success" %}
**Need help with an update or have a question?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}

***

### 1.0.2

#### Changes

* Added nui_callback_strict_mode to fxmanifest
* Fixed banking transaction log type for meteo-phone transfers (phone_deposit -> phone_transfer)
* Fixed shop category check so prices cannot be edited for categories a restaurant does not have access to

#### Modified Files

* `fxmanifest.lua`
* `server\sv_functions.lua`
* `server\sv_owner.lua`
* `server\sv_phone_exports.lua`
* `server\sv_shop.lua`
