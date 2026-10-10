---
description: >-
  Every meteo-racing export a server owner would call - check if a player is
  racing and read driver profiles, race history and the ELO leaderboard.
icon: code
---

# Exports

Check whether a player is tied up in a race and read racing stats from your own scripts, for example a leaderboard board in a garage or a phone app. All exports are server side.

Hosting, joining and running races and the track creator go through the crime tablet, which calls its own set of exports on this script. Those are not listed here.

***

## IsPlayerBusy(source)

`true` while the player is waiting in a race lobby or driving in a race. Use it to stop your own activity from starting mid-race.

```lua
if exports['meteo-racing']:IsPlayerBusy(source) then
    return QBCore.Functions.Notify(source, 'Finish your race first', 'error')
end
```

***

## GetRacerProfile(citizenid, name?)

The full driver card: ELO, tier, global rank, career numbers and favourites.

```lua
local p = exports['meteo-racing']:GetRacerProfile(citizenid)
print(p.elo, p.tier.name, p.rank, p.wins, p.races)
--> 1342   Gold   7   18   64
```

```lua
-- record:
{
    citizenid, name,
    elo, peakElo,
    tier = { name = 'Gold', color = '#F5A623', icon = 'military_tech' },
    rank,                          -- global rank by ELO
    races, rankedRaces, wins, p2, p3, podiums, dnf, offPodium,
    winRate, podiumRate,           -- 0 to 1
    avgPlace,
    cryptoWon, timeRacedMs, tracksMade,
    form,                          -- last 10 ranked results, newest first: { place, finished }
    spark,                         -- last 12 ranked ELO values, oldest first
    favVehicle, favTrack, favClass,
}
```

{% hint style="warning" %}
A player with no racing record gets one created at 1000 ELO the first time this is called. `name` is only used for that new row. They do not show on the leaderboard until they finish a race.
{% endhint %}

**Tiers**

| Tier | From ELO |
| ---- | -------- |
| Bronze | 0 |
| Silver | 1100 |
| Gold | 1300 |
| Platinum | 1500 |
| Diamond | 1700 |
| Apex | 1900 |

***

## GetRaceHistory(citizenid, limit?, offset?)

The player's races, newest first. `limit` defaults to 8 (max 50), `offset` to 0.

```lua
local history = exports['meteo-racing']:GetRaceHistory(citizenid, 5)
print(history.total) --> 64

for _, r in ipairs(history.list) do
    print(r.trackName, r.place, r.fieldSize, r.timeMs, r.eloDelta)
end
--> Vinewood Loop   1   6   182400   18
```

```lua
-- each race:
{
    id, trackName, trackType, difficulty,
    place, fieldSize, ranked, finished,
    timeMs, laps, payout,
    eloDelta,         -- nil for unranked races
    vehicle, vehicleClass,
    ts,               -- unix timestamp
}
```

***

## GetLeaderboard(citizenid?, limit?, offset?)

The ranked leaderboard by ELO. Only drivers who have finished at least one race are listed. `limit` defaults to 25 (max 100). Pass a citizenid to have that player's row flagged with `isSelf`.

```lua
local board = exports['meteo-racing']:GetLeaderboard(nil, 10)
for _, row in ipairs(board.list) do
    print(row.rank, row.name, row.elo, row.tier.name)
end
--> 1   Jane Roe   1912   Apex
--> 2   John Doe   1744   Diamond
```

```lua
-- result:
{
    list = { { rank, name, elo, wins, races, tier, isSelf, citizenid } },
    total = 214,
}
```

***

## GetLeaderboardExtras(citizenid?)

The trend panels: biggest ELO gains this week, most raced tracks and most used cars.

```lua
local extras = exports['meteo-racing']:GetLeaderboardExtras()
for _, m in ipairs(extras.movers) do
    print(m.name, m.gain)
end
--> John Doe   86
```

```lua
-- result:
{
    movers = { { name, elo, gain, tier, isSelf, citizenid } },   -- top 5, last 7 days
    tracks = { { name, track_type, difficulty, times_raced } },  -- top 5
    cars   = { { label, count, pct } },                          -- top 5
}
```

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
