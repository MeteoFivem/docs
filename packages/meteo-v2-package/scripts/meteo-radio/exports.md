---
description: >-
  Every meteo-radio export with a simple example and what it gives back -
  check if a player is on the radio and which channel.
icon: code
---

# Exports

Check the local player's radio from your own client scripts. Both read the channel pma-voice actually has the player on, not the last one the radio asked for, so a rejected join never shows up as connected.

***

## Client

### IsRadioOn()

Is the player connected to any radio channel.

```lua
if exports['meteo-radio']:IsRadioOn() then
    -- they can hear radio traffic
end
```

Returns `true` or `false`.

### GetCurrentChannel()

The channel the player is on, or `0` when they are off the radio.

```lua
local channel = exports['meteo-radio']:GetCurrentChannel()
print(channel) --> 1
```

Returns a number.
