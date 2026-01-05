---
description: Here you can find all the files that can be edited in the escrow version.
---

# Accessible files

<details>

<summary>config.lua</summary>



```lua
Config = {}

-- Configuration for leveling up system and job settings
Config.Main = {
    Debug = false, -- Enable debug mode for developers
    Framework = 'qb-core', -- Specify the framework being used (e.g., 'qb-core')
    Basesalary = 200, -- Base salary when player levels up; salary multiplies by current level
    DefaultRoutesCount = 4, -- Default number of routes displayed on UI
    DefaultXp = 10, -- Amount of XP given after completing a route
    Deposit = 100, -- Deposit amount for vehicle when player starts a new job
    BoxZoneSize = 60, -- Size of the box zone to check if player is near the location
    Npc = 's_m_m_dockwork_01', -- NPC model name
    Npcanim = { -- Animation settings for NPC
        name = 'idle_b',
        dic = 'amb@code_human_police_investigate@idle_a'
    },
    TargetName = 'qb-target' -- Target name
}

-- Main locations
Config.MainLocations = {
    Job = vec4(152.55, -3216.4, 5.9224, 58.7379), -- Job location
    TruckSpawn = vec4(144.48, -3203.96, 5.83, 270.15) -- Truck spawn location
}

-- Job vehicles
Config.JobVehicles = {
    {
        vehiclename  = 'Boxville', -- The name displayed for the vehicle
        vehiclemodel = 'boxville2', -- The spawn code of the vehicle
        image = 'https://docs.fivem.net/vehicles/boxville2.webp', -- Image representation of the vehicle (if available)
        requiredlevel = 1 -- The minimum level required to access this vehicle

    },
    {
        vehiclename  = 'Mule',
        vehiclemodel = 'mule2', 
        image = 'https://docs.fivem.net/vehicles/mule2.webp',
        requiredlevel = 2

    },
    {
        vehiclename  = 'Rumpo', 
        vehiclemodel = 'rumpo2',
        image = 'https://docs.fivem.net/vehicles/rumpo2.webp',
        requiredlevel = 3 
    },
    {
        vehiclename  = 'Pony',
        vehiclemodel = 'pony',
        image = 'https://docs.fivem.net/vehicles/pony.webp',
        requiredlevel = 4

    },
    {
        vehiclename  = 'Benson',
        vehiclemodel = 'benson',
        image = 'https://docs.fivem.net/vehicles/benson.webp',
        requiredlevel = 6

    },
    -- You can add more vehicles below following the same structure
}

-- Rotues locations
Config.RoutesLocations = { --  First Confg.DefaultRoutesCount are default locations that displayed on the job mene
    Custom = { --  You can add any amount of locations here
        Pickup = { -- Custom pickup locations
            vec4(132.66, -3111.52, 5.9, 319.62),
            vec4(116.0271, -2981.9692, 6.0164, 93.8818),
            vec4(131.7200, -3080.8958, 5.8963, 178.7),
            vec4(145.61, -3076.03, 5.9, 178.7),
            vec4(162.72, -2930.66, 6.0, 284.19),
            vec4(159.13, -2871.32, 7.24, 274.24),
            vec4(1218.6489, -3235.5708, 5.5288, 2.9895),
            vec4(1009.7754, -2892.4680, 11.2601, 174.6065),
            vec4(1229.1085, -2999.7224, 9.3193, 90.7288),
            vec4(1197.2217, -3252.3760, 7.0952, 90.1613),
            vec4(1209.3571, -3331.5930, 6.0288, 168.3151),
            vec4(1244.7152, -3240.8279, 6.0288, 287.4425),
            vec4(1179.2863, -3316.3088, 6.0288, 138.3384),
            vec4(1242.8745, -3282.2004, 6.0288, 292.9735),
            vec4(1239.3325, -3173.9116, 7.1049, 291.4469),
            vec4(1224.8906, -3105.9565, 6.0280, 358.9158),
            vec4(1247.2909, -3122.0869, 6.0284, 185.9335),
            vec4(1230.6680, -2910.0261, 9.3193, 92.2997),
            vec4(-106.3983, -2638.7156, 6.0478, 186.4708),
            vec4(46.5556, -2706.6931, 6.0030, 1.6640),

        },

        Delivery = { -- You can add any amount of locations here
            vec4(481.56, -1737.19, 29.15, 159.98),
            vec4(-88.6963, 6493.7466, 32.1007, 232.6438),
            vec4(151.12, -1822.88, 27.49, 43.61),
            vec4(-111.44, -1594.61, 32.0, 234.45),
            vec4(-1168.84, -2022.06, 13.16, 135.52),
            vec4(-583.8513, 195.2310, 71.4421, 86.33),
            vec4(15.1934, -1032.5333, 29.3466, 155.92),
            vec4(1241.89, -396.17, 69.08, 3.06),
            vec4(1664.29, 2.61, 173.78, 129.87),
            vec4(1564.58, 869.71, 77.51, 32.61),
            vec4(796.56, 564.19, 125.92, 319.16),
            vec4(284.36, 943.8, 210.89, 358.46),
            vec4(200.76, 1248.92, 225.46, 216.76),
            vec4(2572.9744, 464.3327, 108.6387, 179.9230),
            vec4(-2963.4468, 432.4125, 15.2777, 118.3108),
            vec4(-439.9847, 1596.8065, 358.4680, 224.5096),
            vec4(-45.8880, 1884.1738, 195.5267, 149.5207),
            vec4(1658.1093, 4840.8286, 42.0322, 278.3586),
            vec4(918.5499, 3655.0923, 32.4771, 3.9190),
            vec4(331.09, -2020.19, 21.73, 137.73),
        },
    }
}

-- Properties for the box carried by the player
Config.PedBoxProp = {
    ["animDict"] = "anim@heists@box_carry@",
    ["animName"] = "idle",
    ["model"] = "hei_prop_heist_box",
    ["bone"] = 60309,
    ["x"] = 0.025,
    ["y"] = 0.08,
    ["z"] = 0.255,
    ["xR"] = -145.0,
    ["yR"] = 290.0,
    ["zR"] = 0.0,
}

-- Language configurations
Config.Lang = {
    blipname = 'Los Santos Trucker',
    depositcash = ''..Config.Main.Deposit..' Deposit paid with cash for vehicle',
    depositbank = ''..Config.Main.Deposit..' Deposit paid from bank for vehicle',
    depositrequired = ''..Config.Main.Deposit..' Deposit required for vehicle',
    depositreturn = ''..Config.Main.Deposit..' Deposit paid for returning vehicle',
    earnxp = 'You have earned xp',
    errorMessages = {
        noNewRoutes = 'There are no new routes...',
        alreadyOnJob = 'You are already on a job.',
        vehicleDestroyed = 'Your vehicle has been destroyed.',
        notRightVehicle = 'Not in the right vehicle.',
        tooFarFromPickup = 'Too far from pickup location.',
        loadCargo = 'Please load the cargo onto the vehicle.',
        getOutVehicle = 'Please get out from the vehicle.',
        tooFarFromDeliver = 'You are too far from the delivery location.',
        pickupCargo = 'You need to pick up cargo from the vehicle.',
        vehicleNotValid = 'Your vehicle is not near or not valid.'
    },
    successMessages = {
        proceedDeliverNPC = 'Please proceed to deliver the cargo to the NPC.',
        proceedToDestination = 'Your delivery destination awaits. Please proceed to the specified location.',
        getPkgFromNPC = 'Go to the location and get package from NPC.',
        cargoDelivered = 'You have successfully delivered the cargo.',
        headOverToLoadCargo = 'Head over to the vehicle to load the cargo box.',
        returnVehicle = 'Please return the vehicle to the location.',
        returnVehicleSuccess = 'You have successfully returned the vehicle.',
        newPayment = 'You have earned $'
    },
    targetMessages = {
        openJob = 'Open Trucker Job',
        unLoadPkg = 'Unload the cargo box',
        LoadPkg = 'Load cargo box to vehicle'
    }
}
```

</details>

<details>

<summary>cl_open.lua</summary>



```lua
local QBCore = exports[Config.Main.Framework]:GetCoreObject()

-- Function to notify the trucker
function truckerNotify(text, type)
    QBCore.Functions.Notify(text, type)
end

-- Function to set a vehicle fuel
function setTruckFuel(vehcle)
    exports['LegacyFuel']:SetFuel(vehcle, 100.0) -- you can add any fuel script you want.
end

-- Function to give keys to a vehicle
function giveKeys(vehplate)
    TriggerEvent("vehiclekeys:client:SetOwner", vehplate)
end

-- Function to add a target entity for interaction
function AddTarget(entity, targettype, targeevent, targeicon, targelabel)
    exports[Config.Main.TargetName]:AddTargetEntity(entity, {
        options = {
            {
                type = targettype,
                event = targeevent,
                icon = targeicon,
                label = targelabel,
            },
        },
        distance = 3.0
    })
end

-- Function to remove a target entity
function RemoveTarget(entity)
    exports[Config.Main.TargetName]:RemoveTargetEntity(entity)
end

-- Function to display a progress bar for a task
function progress(name, callback)
    local ped = PlayerPedId()
    Wait(500)
    QBCore.Functions.Progressbar("work_dropbox", name, 2000, false, true, {
        disableMovement = true,
        disableCarMovement = true,
        disableMouse = false,
        disableCombat = true,
    }, {}, {}, {}, function()
        callback(true)
        StopAnimTask(ped, "anim@gangops@facility@servers@", "hotwire", 1.0)
    end, function()
        truckerNotify('cancelled', "error")
        StopAnimTask(ped, "anim@gangops@facility@servers@", "hotwire", 1.0)
        callback(false)
    end)
end

```

</details>

<details>

<summary>sv_open.lua</summary>



```lua
function truckerNotify(source, text, type)
    TriggerClientEvent('QBCore:Notify', source, text, type)
end
```

</details>
