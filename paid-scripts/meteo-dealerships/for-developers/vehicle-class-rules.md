---
description: >-
  How vehicle classes (S, A, B, C, D, E) are automatically assigned when
  importing vehicles.
---

# Vehicle Class Rules

## How are vehicle classes determined?

Classes are assigned automatically in this order:

| Priority | Source | Description |
|----------|--------|-------------|
| 1st | `customclass` | QBCore vehicle with `customclass = 'S'` field |
| 2nd | Category | Based on vehicle category (super, sports, etc.) |
| 3rd | Price | Based on price thresholds |
| 4th | Default | Falls back to D class |

***

## Class Overview

| Class | Vehicles |
|-------|----------|
| S | Supercars, hypercars |
| A | Sports cars, aircraft |
| B | Muscle, sports classics |
| C | Coupes, sedans, motorcycles |
| D | Compacts, SUVs, offroad |
| E | Vans, industrial, utility |

***

## How do I override a vehicle's class?

Add `customclass` to your vehicle config:

**QBCore** - `qb-core/shared/vehicles.lua`:

```lua
{ model = 'meteoc17', name = 'Dominator GT CTX C3', brand = 'Vapid', price = 80000, category = 'custom', type = 'automobile', shop = 'pdm', customclass = 'C' },
```

**QBox** - `shared/vehicles.lua`:

```lua
meteoc17 = {
    name = 'Dominator GT CTX C3', brand = 'Vapid', model = 'meteoc17',
    price = 80000, category = 'custom', type = 'automobile',
    hash = `meteoc17`, customclass = 'C',
},
```

The `customclass` field overrides all automatic rules.

***

## Default Category Rules

| Category | Class |
|----------|-------|
| super | S |
| sports | A |
| muscle | B |
| sportsclassics | B |
| coupes | C |
| sedans | C |
| motorcycles | C |
| compacts | D |
| suvs | D |
| offroad | D |
| vans | E |
| industrial | E |

***

## Default Price Rules

If category isn't mapped, price determines class:

| Price | Class |
|-------|-------|
| $1,500,000+ | S |
| $500,000+ | A |
| $150,000+ | B |
| $50,000+ | C |
| Below $50,000 | D |
