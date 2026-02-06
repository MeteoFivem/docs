# Vehicle Class Rules

Vehicle classes (S, A, B, C, D, E) are automatically assigned when importing vehicles from QBCore.

## Priority Order

1. **QBCore `customclass`** - If the vehicle in `QBCore.Shared.Vehicles` has a `customclass` field, it takes priority
2. **Category rules** - `Config.classRules.byCategory` mapping
3. **Price rules** - `Config.classRules.byPrice` thresholds
4. **Default** - `Config.classRules.default` (fallback)

## QBCore Override

Add `customclass` to any vehicle in QBCore to override automatic class assignment:

```lua
-- In qb-core/shared/vehicles.lua
    { model = 'meteoc41',  name = 'Tempesta CTX',            brand = 'Pegassi',      price = 1300000, category = 'custom', type = 'automobile', shop = 'pdm', customclass = 'S' },
```

## Configuration

In `shared/config.lua`:

```lua
Config.classRules = {
    -- Category-based class assignment
    byCategory = {
        super = 'S',
        sports = 'A',
        muscle = 'B',
        -- etc.
    },

    -- Price-based fallback (if category not mapped)
    byPrice = {
        { min = 1500000, class = 'S' },
        { min = 500000,  class = 'A' },
        { min = 150000,  class = 'B' },
        { min = 50000,   class = 'C' },
        { min = 0,       class = 'D' },
    },

    -- Default if nothing matches
    default = 'D'
}
```

## Classes

| Class | Typical Use |
|-------|-------------|
| S | Super cars, hypercars, special vehicles |
| A | Sports cars, performance vehicles, aircraft |
| B | Muscle, sports classics |
| C | Coupes, sedans, motorcycles, boats |
| D | Compacts, SUVs, offroad |
| E | Vans, industrial, utility, economy |
