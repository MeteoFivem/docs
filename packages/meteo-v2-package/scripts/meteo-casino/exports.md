---
description: >-
  Every meteo-casino export with a simple example and what it gives back -
  house profit, per game and per player numbers, big wins, live tables and
  the PA announcer.
icon: code
---

# Exports

Read casino numbers from an admin menu, a website or a Discord bot. Everything is server side and read only, apart from `playAnnouncement`.

Numbers come from daily stat tables, so the calls stay cheap on a busy floor. `days` is clamped to 1-365 and defaults to 7.

***

## House

### GetHouseSummary(days?)

What the casino made over the last `days`, and how many chips players are holding.

```lua
local summary = exports['meteo-casino']:GetHouseSummary(30)
print(json.encode(summary))
--> { "rounds": 8421, "wagered": 5120000, "paidOut": 4890000, "profit": 230000,
-->   "chipsInPlay": 550000, "players": 87 }
```

| Field | Notes |
| ----- | ----- |
| `profit` | `wagered - paidOut`, the house's profit |
| `chipsInPlay` | Every chip ever bought minus every chip sold back. All time, not limited to `days` |
| `players` | Distinct players who played in the window |

### GetGameTotals(days?)

One row per game, busiest first. Games are `slots`, `blackjack`, `roulette`, `wheel` and `cashier`.

```lua
for _, row in ipairs(exports['meteo-casino']:GetGameTotals(7)) do
    print(row.game, row.rounds, row.wagered, row.paidOut, row.profit)
end
--> slots       5120   2400000   2210000   190000
--> blackjack   1180   1300000   1265000    35000
```

### GetDailyTotals(days?)

One row per day, oldest first. Good for a graph.

```lua
for _, row in ipairs(exports['meteo-casino']:GetDailyTotals(14)) do
    print(row.day, row.wagered, row.paidOut, row.profit)
end
--> 2026-09-28   410000   392000   18000
```

***

## Players

### GetPlayerTotals(citizenid, days?)

One player's numbers per game, plus their totals. Returns `nil` if `citizenid` is not a string.

```lua
local stats = exports['meteo-casino']:GetPlayerTotals('ABC12345', 30)
print(stats.total.wagered, stats.total.profit) --> 85000  -12000
```

```lua
{
    games = { { game = 'slots', rounds = 40, wagered = 60000, paidOut = 72000, biggestWin = 25000, profit = -12000 } },
    total = { rounds = 40, wagered = 60000, paidOut = 72000, biggestWin = 25000, profit = -12000 },
}
```

`profit` here is the **house's** profit, so a player who is up shows a negative number.

### GetTopPlayers(days?, limit?, order?)

Biggest winners or losers. `order` is `'winners'` (default) or `'losers'`. `limit` defaults to 10 and is clamped to 1-100.

```lua
for i, p in ipairs(exports['meteo-casino']:GetTopPlayers(7, 5)) do
    print(i, p.name, p.profit)
end
--> 1   Ava Dorn    175000
--> 2   John Doe     42000
```

Each row has `citizenid`, `name`, `rounds`, `wagered`, `paidOut`, `biggestWin` and `profit`. Here `profit` is the **player's**, so a winner is positive.

***

## Events and Live State

### GetEvents(limit?)

Recent notable events, newest first. `limit` defaults to 50 and is clamped to 1-200.

```lua
for _, e in ipairs(exports['meteo-casino']:GetEvents(10)) do
    print(e.createdAt, e.type, e.name, e.amount)
end
--> 2026-09-18 21:04:11   big_win   Ava Dorn   175000
```

```lua
-- each event:
{ type = 'big_win', game = 'slots', amount = 175000, citizenid = 'ABC12345',
  name = 'Ava Dorn', createdAt = '2026-09-18 21:04:11', meta = { ... } }
```

`type` is one of `big_win`, `vehicle_won`, `chips_bought`, `chips_sold`, `pending`. `meta` is already decoded.

### GetLiveState()

What is happening right now, straight from memory with no query.

```lua
local live = exports['meteo-casino']:GetLiveState()
print(json.encode(live))
--> { "openStakes": 45000, "openBets": 6, "inCasino": 11 }
```

| Field | Notes |
| ----- | ----- |
| `openStakes` | Chips riding on a table right now |
| `openBets` | How many open bets that is |
| `inCasino` | Players inside the casino zone |

***

## PA Announcer

### playAnnouncement(speechType)

Plays a PA line to everyone inside the casino. Returns `false` for an unknown line, or when another line played less than 4 seconds ago.

```lua
exports['meteo-casino']:playAnnouncement('slotJackpot')
```

Lines: `newVehicle`, `champagneBought`, `straightFlushWin`, `slotJackpot`, `motorcycleWon`, `vehicleWon`.

{% hint style="info" %}
`playAnnouncement` keeps the same name the old meteo-casinoannounce script used, so code that called it keeps working once you point it at `exports['meteo-casino']`.
{% endhint %}
