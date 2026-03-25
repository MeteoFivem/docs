---
description: How to add new food items, drinks, and recipes to Meteo Restaurants.
---

# Adding Items

***

### Overview

Adding a new item takes up to 5 steps depending on the item type:

| Step | File                                                      | When                |
| ---- | --------------------------------------------------------- | ------------------- |
| 1    | `shared/items.lua` - Ingredients                          | Raw materials       |
| 2    | `shared/items.lua` - Processed                            | Needs processing    |
| 3    | `shared/items.lua` - Recipes                              | All craftable items |
| 4    | `shared/items.lua` - Usables                              | Consumable items    |
| 5    | `qb-core/shared/items.lua` or `qbx_core/shared/items.lua` | All items           |

***

### Step 1: Add Ingredient

```lua
-- shared/items.lua -> Items.ingredients
meteo_tuna = { label = 'Tuna', category = 'meals', price = 4 },
```

| Field      | Description                                     |
| ---------- | ----------------------------------------------- |
| `label`    | Display name                                    |
| `category` | Which category (drinks, meals, etc.)            |
| `price`    | Cost at ingredients shop (from restaurant bank) |

***

### Step 2: Add Processed Item (Optional)

Only needed if the ingredient needs processing before cooking.

```lua
-- shared/items.lua -> Items.processed
meteo_scrambled_eggs = {
    label = 'Scrambled Eggs',
    category = 'meals',
    fromIngredient = 'meteo_eggs',
    processType = 'blend'
},
```

#### Process Types

| Type    | Duration | Use For            |
| ------- | -------- | ------------------ |
| `chop`  | 4s       | Cutting vegetables |
| `grind` | 5s       | Grinding meat      |
| `blend` | 3s       | Mixing, scrambling |

***

### Step 3: Add Recipe

```lua
-- shared/items.lua -> Items.recipes
meteo_tunasandwich = {
    label = 'Tuna Sandwich',
    category = 'meals',
    price = 14,
    maxPrice = 40,
    stressRelief = 3,
    steps = {
        { type = 'assemble', inputs = { 'meteo_bread', 'meteo_tuna', 'meteo_mayo', 'meteo_lettuce' }, output = 'meteo_tunasandwich' },
    }
},
```

| Field          | Description                                |
| -------------- | ------------------------------------------ |
| `category`     | Decides which station can make it          |
| `price`        | Default sell price                         |
| `maxPrice`     | Max price owner can set                    |
| `stressRelief` | Stress reduction on use (optional)         |
| `directSale`   | Set `true` for items sold without crafting |

#### Recipe Types - Cooking Station

| Type       | Duration | Use For         |
| ---------- | -------- | --------------- |
| `grill`    | 8s       | Grilled items   |
| `fry`      | 6s       | Fried items     |
| `bake`     | 10s      | Baked items     |
| `assemble` | 4s       | Cold assembly   |
| `cook`     | 8s       | General cooking |

#### Recipe Types - Drink Station

| Type   | Duration | Use For            |
| ------ | -------- | ------------------ |
| `pour` | 2s       | Sodas, cold drinks |
| `brew` | 8s       | Coffee, tea        |
| `mix`  | 4s       | Mixed drinks       |

***

### Step 4: Add Usable

```lua
-- shared/items.lua -> Items.usables
meteo_tunasandwich = {
    label = 'Tuna Sandwich',
    type = 'eat',
    hunger = 30,
    thirst = -5,
    stressRelief = 3,
},
```

#### Usable Types

| Type       | Animation       | Use For            |
| ---------- | --------------- | ------------------ |
| `eat`      | Eating burger   | Food items         |
| `drink`    | Drinking bottle | Cold drinks, sodas |
| `drinkCup` | Drinking coffee | Hot drinks in cups |

#### Custom Props (Optional)

```lua
meteo_sundae = {
    label = 'Sundae',
    type = 'eat',
    hunger = 18,
    thirst = 8,
    prop = {
        model = 'pata_christmasfood7',
        bone = 60309,
        pos = vec3(-0.046, 0.00, -0.03),
        rot = vec3(0.0, 0.0, -50.0),
    },
    propTwo = {
        model = 'h4_prop_h4_coke_spoon_01',
        bone = 28422,
        pos = vec3(0.0, 0.0, 0.0),
        rot = vec3(0.0, 20.0, 0.0),
    },
},
```

| Bone ID | Description      |
| ------- | ---------------- |
| `60309` | Right hand       |
| `28422` | Left hand        |
| `18905` | Right hand (alt) |

***

### Step 5: Add to QBCore

**Ingredients (not usable):**

```lua
meteo_tuna = { name = 'meteo_tuna', label = 'Tuna', weight = 150, type = 'item', image = 'meteo_tuna.png', unique = false, useable = false, shouldClose = false, description = 'Fresh tuna' },
```

**Final products (usable):**

````lua
meteo_tunasandwich = { name = 'meteo_tunasandwich', label = 'Tuna Sandwich', weight = 300, type = 'item', image = 'meteo_tunasandwich.png', unique = true, useable = true, shouldClose = true, description = 'Fresh tuna sandwich with lettuce' },
```<div data-gb-custom-block data-tag="hint" data-style='warning'>Final products **must** have `unique = true` for quality/metadata to work. Without this, the multi-use quality won't work.</div>

***

## Direct Sale Items

For items sold without crafting (e.g., water bottles):

```lua
water_bottle = {
    label = 'Water Bottle',
    category = 'drinks',
    price = 5,
    maxPrice = 15,
    directSale = true,
    steps = {}
},
````

***

### Checklist

* Item name uses `meteo_` prefix
* Added to `Items.ingredients` (if raw ingredient)
* Added to `Items.processed` with `processType` (if needs processing)
* Added to `Items.recipes` with correct category and step type
* Added to `Items.usables` with correct type (eat/drink/drinkCup)
* Added to `qb-core/shared/items.lua` or `qbx_core/shared/items.lua` with `unique = true` for final products
* `stressRelief` matches in both recipe and usable (if used)
* Added item image to inventory
