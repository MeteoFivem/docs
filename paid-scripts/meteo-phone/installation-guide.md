---
description: >-
  Installation guide for Meteo Studios FiveM Phone. You must carefully follow
  all the steps that you will see in this installation guide.
---

# Installation guide

{% hint style="info" %}
Purchase This Script from: [Meteo FiveM Phone](https://meteo.tebex.io/package/7185377)
{% endhint %}



{% stepper %}
{% step %}
### Download the Phone

* Visit [Cfx Portal](https://portal.cfx.re/)
* Login and go to assets tab
* Find **"Meteo Studios Phone"** and download it


{% endstep %}

{% step %}
### Install the Files

* Unzip the downloaded file
* Put it in a folder called `[meteostudios]` (or your existing resource folder)
* Open your **server.cfg** file
* Add this line: `ensure [meteostudios]`<br>


{% endstep %}

{% step %}
### Install Required Resources

Download and update these resources (get the latest versions)

* [ox\_lib](https://github.com/overextended/ox_lib/releases) - (just update with latest version)
* [oxmysql ](https://github.com/overextended/oxmysql/releases)- (just update with latest version)
* [screencapture](https://github.com/itschip/screencapture/releases) - (qbox already have this. but make sure)
* [meteo-keybinddisplay](https://github.com/MeteoStudios/meteo-keybinddisplay) - (required!)&#x20;

make sure they're all added in your server.cfg


{% endstep %}

{% step %}
### Setup Database

* Open **HeidiSQL** (database tool)
* Find the file: `meteo-phone/install/meteo_phone.sql`
* Run this SQL file in your database


{% endstep %}

{% step %}
### Add Phone Items to Inventory

#### Add Items:

1. Go to `meteo-phone/install/qbox/`
2. Open **ox-items.md**
3. Copy all items into your `ox_inventory/data/items.lua` file

{% hint style="warning" %}
**Important:** Delete your old phone item from your previous phone system (probably NPWD)
{% endhint %}

#### Add Weapons (if needed):

1. Open **ox-weapons.md**
2. Copy all items into your `ox_inventory/data/weapons.lua` file

#### Add Images:

Copy all images from `meteo-phone/install/images/` to `ox_inventory/web/images/`


{% endstep %}

{% step %}
### Remove Old NPWD Phone (If You Have It)

Delete code in `ox_inventory/client.lua` (around line 1241):

```lua
-- Comment out or delete this:
local phone = Items.phone
if phone and phone.count < 1 then
    pcall(function()
        return exports.npwd:setPhoneDisabled(true)
    end)
end
```

Delete code in `ox_inventory/modules/items/client.lua` (around line 132):

```lua
-- Comment out or delete this:
Item('phone', function(data, slot)
    local success, result = pcall(function()
        return exports.npwd:isPhoneVisible()
    end)
    if success then
        exports.npwd:setPhoneVisible(not result)
    end
end)
```

#### Remove NPWD completely:

1. Delete `[npwd]` and `[npwd-apps]` folders from your server
2. Remove NPWD lines from **server.cfg**


{% endstep %}

{% step %}
### Add Companies to Phone App

To display your server's companies/jobs in the phone's Companies app, you need to update your jobs configuration.

#### Edit Jobs File

1. Go to `[qbx]/qbx_core/shared/jobs.lua`
2. For each job you want to show in the phone, add two properties:
   * `icon` - Material icon name for the job
   * `showInPhone` - Set to `true` to display in Companies app

#### Example Configuration:

```lua
['police'] = {
    label = 'LSPD',
    type = 'leo',
    defaultDuty = true,
    offDutyPay = false,
    icon = 'local_police',        -- Material Icon for phone app
    showInPhone = true,            -- Show in phone Companies app
    grades = {
        [0] = {
            name = 'Recruit',
            payment = 50
        },
        [1] = {
            name = 'Officer',
            payment = 75
        },
        [2] = {
            name = 'Sergeant',
            payment = 100
        },
        [3] = {
            name = 'Lieutenant',
            payment = 125
        },
        [4] = {
            name = 'Chief',
            isboss = true,
            bankAuth = true,
            payment = 150
        },
    },
},
```

#### Material Icons Reference

You can find Material icon names at: [https://fonts.google.com/icons](https://fonts.google.com/icons)

**Common job icons:**

* Police: `local_police`
* EMS: `local_hospital`
* Mechanic: `build`
* Taxi: `local_taxi`
* Real Estate: `home`
* Car Dealer: `directions_car`

#### Apply to All Jobs

Repeat this process for every job you want visible in the phone:

```lua
icon = 'icon_name_here',
showInPhone = true,
```

{% hint style="warning" %}
**Note:** Jobs without `showInPhone = true` will NOT appear in the phone's Companies app.
{% endhint %}


{% endstep %}
{% endstepper %}

***

### Quick Checklist

* Installed in server folder
* Added to server.cfg
* Installed all dependencies
* Ran SQL file
* Added items to inventory
* Added images to inventory
* Removed old NPWD phone code
* Deleted NPWD folders and config

***

### Next Steps

Now the meteo phone installation part is done. You now need to configure the phone to work with your server settings.

**Continue to** [**Configuration Guide**](https://docs.meteofivem.net/paid-scripts/meteo-phone/configuration-guide) to set up your phone properly.

***

**Need Help?**

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)

