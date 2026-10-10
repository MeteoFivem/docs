---
description: >-
  Config options, customization, and how to integrate Meteo Restaurants with
  other resources.
---

# For Developers

### Customization

#### Currency Symbol

Change currency in `shared/config.lua`:

```lua
Config.currencySymbol = '$'   -- US Dollar
Config.currencySymbol = '€'   -- Euro
Config.currencySymbol = '£'   -- British Pound
```

#### Multi-Language

Uses **ox\_lib locale**. Translate to any language:

| File              | Purpose           |
| ----------------- | ----------------- |
| `locales/en.json` | English (default) |
| `locales/de.json` | German            |
| `locales/es.json` | Spanish           |
| `locales/fr.json` | French            |

Create your own locale file and set it in ox\_lib. All UI text, notifications, and menus translate automatically.

***

### Employees

#### Grades

Grades and permissions are set in `shared/config.lua`:

| Grade | Label      | Paycheck | Key Permissions                                |
| ----- | ---------- | -------- | ---------------------------------------------- |
| 0     | Employee   | $50      | Cook, storage, orders                          |
| 1     | Supervisor | $75      | + clock others, force clock out                |
| 2     | Manager    | $100     | + hire/fire, view earnings, pay commissions    |
| 3     | Owner      | $0       | All permissions                                |

#### Permissions

| Category    | Permissions                                                      |
| ----------- | ---------------------------------------------------------------- |
| Basic Work  | cook, storage, orders, cancelOrder                               |
| Employees   | clockOthers, hire, fire, forceClockOut, viewLogs                 |
| Banking     | viewEarnings, deposit, withdraw, payCommission, payBonus, editCommissionRate |
| Management  | manageRestaurant, transferOwnership, editPrices, toggleShop, announce |
| Applications | manageApplications                                              |

***

### Commissions

* Rate per restaurant (5% - 25%, default 15%)
* Employees earn commission when completing orders
* Managers can view and pay commissions
* Performance tracked per employee per day

***

### Paychecks

Auto paychecks for clocked-in employees:

| Setting          | Default | Description                    |
| ---------------- | ------- | ------------------------------ |
| `enabled`        | true    | Enable/disable paychecks       |
| `interval`       | 10      | Minutes between paychecks      |
| `payFromBank`    | false   | Pay from restaurant bank or not |
| `notifyEmployee` | true    | Notify employee on payment     |

***

### Work Zones

Auto clock-out when employees leave the area:

| Setting           | Default | Description                        |
| ----------------- | ------- | ---------------------------------- |
| `enabled`         | true    | Enable auto clock-out              |
| `defaultRadius`   | 50.0    | Work zone radius in meters         |
| `warningDistance`  | 10.0    | Warning distance from edge         |
| `graceTime`       | 10000   | Grace period before clock-out (ms) |

***

### Stations

Each restaurant can have these location types:

| Station          | Purpose                      |
| ---------------- | ---------------------------- |
| clock            | Clock in/out and manage menu |
| ingredients      | Buy ingredients              |
| kitchenStorage   | Shared kitchen storage       |
| shopStash        | Shop stash for customers     |
| personalStash    | Personal employee locker     |
| process          | Process raw ingredients      |
| cooking          | Cook recipes (meals, desserts) |
| drink            | Make drinks                  |
| order            | Take and manage orders       |
| applicationPed   | Job application NPC          |

***

### Categories

Enable categories per restaurant to control which items are available:

| Category          | Type     | Items                            |
| ----------------- | -------- | -------------------------------- |
| drinks            | Drink    | Sodas, coffee, tea               |
| desserts          | Cooking  | Donuts, ice cream, sundaes       |
| meals             | Cooking  | Chicken, rice, sandwiches, tacos |
| luckyplucker      | Cooking  | Lucky Plucker menu               |
| pizzathis         | Cooking  | Pizza This menu                  |
| burgershot        | Cooking  | Burgershot menu                  |
| wigwam            | Cooking  | Wigwam menu                      |
| upnatom           | Cooking  | Up-n-Atom menu                   |
| cluckinbell       | Cooking  | Cluckin' Bell menu               |

***

### Phone

Supports notifications for employee events:

| Resource        | Features                                         |
| --------------- | ------------------------------------------------ |
| **meteo-phone** | Full support - notifications, banking, announcements |
| **high-phone**  | Basic notifications                              |
| **qb-phone**    | Basic notifications                              |
| **npwd**        | Basic notifications                              |

***

### Database

Uses its own tables, no changes to core QBCore tables:

| Table                              | Purpose              |
| ---------------------------------- | -------------------- |
| `meteo_restaurants`                | Restaurant data      |
| `meteo_restaurant_locations`       | Station locations     |
| `meteo_restaurant_employees`       | Employee records     |
| `meteo_restaurant_doors`           | Doorlock data        |
| `meteo_restaurant_orders`          | Order history        |
| `meteo_restaurant_work_logs`       | Activity logs        |
| `meteo_restaurant_performance`     | Employee performance |
| `meteo_restaurant_earnings`        | Earnings history     |
| `meteo_restaurant_banking_logs`    | Banking transactions |
| `meteo_restaurant_shop_logs`       | Shop sales           |

***

### Need Help?

* Support: <a href="http://discord.meteofivem.net/" target="_blank">Meteo Studios Discord</a>
