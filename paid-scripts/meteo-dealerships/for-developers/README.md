---
description: >-
  Everything you need to know about Meteo Dealerships integration,
  customization, and why it's the best qb-vehicleshop, qbx_vehicleshop
  alternative.
---

# For Developers

### Zero Migration Hassle

Meteo Dealerships is designed as a **drop-in replacement** for qb-vehicleshop, qbx\_vehicleshop. Same QBCore/QBox vehicle system, premium features, better price.

#### Feature Comparison

<table><thead><tr><th>Feature</th><th width="166">qb-vehicleshop/qbx_vehicleshop</th><th>Meteo Dealerships</th></tr></thead><tbody><tr><td><strong>Player-Owned Dealerships</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Finance System</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Repossession System</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Audit Logs</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>In-Game Price Editing</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Employee Management</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Limited Time Offers</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Multi-Language Support</strong></td><td>Limited</td><td>Full</td></tr><tr><td><strong>Admin Panel</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Phone Notifications</strong></td><td>No</td><td>Yes</td></tr><tr><td><strong>Affordable Price</strong></td><td>Free</td><td>$</td></tr></tbody></table>

> Works with your existing QBCore/QBox `shared/vehicles.lua` - just import and go.

***

### Full Customization

#### Currency Symbol

Change currency for any region in `shared/config.lua`:

```lua
Config.currencySymbol = '$'   -- US Dollar
Config.currencySymbol = '€'   -- Euro
Config.currencySymbol = '£'   -- British Pound
Config.currencySymbol = 'Kč'  -- Czech Koruna
Config.currencySymbol = 'R$'  -- Brazilian Real
```

#### Multi-Language Support

Full **ox\_lib locale** integration. Translate to any language:

| File              | Purpose           |
| ----------------- | ----------------- |
| `locales/en.json` | English (default) |
| `locales/de.json` | German            |
| `locales/es.json` | Spanish           |
| `locales/fr.json` | French            |

Create your own locale file and set it in ox\_lib. All UI text, notifications, and menus translate automatically.

***

### In-Game Management

#### Admin Panel (`/dealeradmin`)

No config file editing needed for common tasks:

| Feature             | Description                            |
| ------------------- | -------------------------------------- |
| **Import Vehicles** | Pull from QBCore/QBox shared vehicles  |
| **Set Owners**      | Assign dealership ownership to players |
| **Manage Catalog**  | Add/remove vehicles from dealerships   |
| **View All Sales**  | Track sales across all dealerships     |

#### Owner/Manager Features

Dealership owners and managers can do everything in-game:

| Feature                 | Description                           |
| ----------------------- | ------------------------------------- |
| **Edit Prices**         | Change vehicle prices without restart |
| **Order Stock**         | Purchase inventory at wholesale       |
| **Hire/Fire**           | Manage employees and grades           |
| **Set Featured**        | Highlight vehicles in shop            |
| **Limited Time Offers** | Create timed discounts                |
| **Banking**             | Deposit/withdraw dealership funds     |

> **No server restarts** required for price changes or inventory updates.

***

### Finance System

Full vehicle financing with configurable terms:

| Feature                 | Description                      |
| ----------------------- | -------------------------------- |
| **Down Payment**        | Configurable minimum percentage  |
| **Payment Terms**       | Up to 24 months                  |
| **Interest Rate**       | Configurable percentage          |
| **Payment Intervals**   | Real-time payment schedules      |
| **Overdue Tracking**    | Automatic late payment detection |
| **Phone Notifications** | Payment reminders via phone      |

Players can finance vehicles, make payments at dealership NPCs, and track their loans.

***

### Repossession System

Automatic vehicle repo for missed payments:

| Feature              | Description                                  |
| -------------------- | -------------------------------------------- |
| **Grace Period**     | Configurable time before repo                |
| **Overdue Warnings** | Notifications before repossession            |
| **Vehicle Recovery** | Players can pay to recover repo'd vehicles   |
| **Recovery Penalty** | Configurable fee percentage                  |
| **Blacklist System** | Block repeat offenders from financing        |
| **Admin Override**   | Clear blacklist via `/clearfinanceblacklist` |

Repossessed vehicles are removed from player ownership until recovered with penalty fee.

***

### Audit Logs

Complete activity tracking for dealership owners:

| Log Type             | What's Tracked                                   |
| -------------------- | ------------------------------------------------ |
| **Sales**            | Every vehicle sold, buyer, price, payment method |
| **Purchases**        | Inventory orders, wholesale costs                |
| **Employee Actions** | Hires, fires, grade changes                      |
| **Price Changes**    | Who changed what price, when                     |
| **Banking**          | Deposits, withdrawals, by whom                   |
| **Finance**          | Payments received, overdue accounts              |

Owners can view full audit history in the manage menu. Admins can access via admin panel.

***

### Requirements

#### Core Dependencies

| Dependency                      | Purpose                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------- |
| **ox\_lib**                     | Callbacks, locale, and UI components                                                  |
| **oxmysql**                     | Database queries                                                                      |
| **ox\_target** or **qb-target** | Interaction zones (auto-detected)                                                     |
| **meteo-keybinddisplay**        | Keybind prompts ([free script](https://github.com/MeteoStudios/meteo-keybinddisplay)) |

#### Optional Integrations

| Resource          | Feature                                |
| ----------------- | -------------------------------------- |
| **meteo-phone**   | Finance notifications, employee alerts |
| **qb-phone/npwd** | Basic notification support             |

***

### Export Integration

Check if vehicles are financed before allowing sales in your scripts:

```lua
-- Server-side
local result = exports['meteo-dealerships']:isVehicleFinanced(plate)

if result.financed then
    -- Block sale, show remaining balance
    print('Balance: $' .. result.data.balanceRemaining)
end
```

See [Useful Exports](useful-exports.md) for all available exports.

***

### Database

Uses standard QBCore/QBox patterns. Finance data stored separately:

| Table                | Purpose                                |
| -------------------- | -------------------------------------- |
| `player_vehicles`    | Standard QBCore/QBox vehicle ownership |
| `meteo_dealership_*` | Dealership data, finance, employees    |

No modifications to core QBCore tables.

***

### Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)

***

### Quick Summary

* **Affordable jg-dealerships alternative** - Premium features, better price
* Drop-in **qb-vehicleshop replacement**
* Works with **qbx\_vehicleshop** servers migrating
* **Finance system** with configurable terms and interest
* **Repossession system** with recovery and blacklist
* **Audit logs** for complete activity tracking
* **Multi-language** support via ox\_lib locale
* **Config.currencySymbol** for any currency
* **In-game price editing** - no restarts
* Player-owned dealerships with **employee system**
* **Limited Time Offers** for promotions
* Full **admin panel** for management
* **Phone notifications** via meteo-phone
* **QBCore and QBox** compatible
