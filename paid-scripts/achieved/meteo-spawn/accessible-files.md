---
description: Here you can find all the files that can be edited in the escrow version.
---

# Accessible files



<details>

<summary>config.lua</summary>



```lua
Config = {}

Config.Main = {
    debugMode = false, -- Set to true to display debug messages (For Developers)
    defaultNormalImg = 'images/location.png', -- Default image for normal locations
    defaultHouseImg = 'images/house.png', -- Default image for houses
    defaultApartmentImg = 'images/building.png', -- Default image for apartments
    autoJail = true -- Set to true to automatically jail players after respawn (if player has jail time)
}

Config.psHousing = false -- If you are using ps-housing set this as true -- https://github.com/Project-Sloth/ps-housing -- Also don't forget to remove '@qb-apartments/config.lua' in fxmanifest.lua

Config.DefaultSpawns = { -- Default Locations
    [1] = {
        label = 'Legion Square',
        coords = vector4(195.17, -933.77, 29.7, 144.5),
    },
    [2] = {
        label = 'Mirror Park',
        coords = vector4(1127.14, -645.29, 55.79, 281.89),
    },
    [3] = {
        label = 'Police Department',
        coords = vector4(428.23, -984.28, 29.76, 3.5),
    },
    [4] = {
        label = 'Paleto Bay',
        coords = vector4(80.35, 6424.12, 31.67, 45.5),
    },
    [5] = {
        label = 'Motels',
        coords = vector4(327.56, -205.08, 53.08, 163.5),
    },
    [6] = {
        label = 'Sandy Shores',
        coords = vector4(2050.31, 3727.03, 32.91, 219.25),
    },
    -- Add more here
}
```

</details>
