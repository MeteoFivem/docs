---
description: >-
  Use the in-game creator tool to add rooms to your apartment complex. No code
  editing needed.
---

# Creating Rooms

This guide shows you how to use the built-in apartment creator to add rooms to your complex.

***

## Before You Start

You need:

1. A complex already configured (see [Adding New Complex](adding-new-complex.md))
2. Your MLO installed and working in-game
3. Debug mode enabled

## Enable Debug Mode

{% stepper %}
{% step %}
#### Turn on Debug Mode

Open `meteo-apartments/shared/config.lua` and set debug to true:

```lua
Config.debug = true
```

{% hint style="warning" %}
**Debug mode is required** to use the `/aptdev` command and creator tools.
{% endhint %}
{% endstep %}

{% step %}
#### Restart the Resource

Debug mode is now active. You can use developer commands.
{% endstep %}
{% endstepper %}

***

## Using the Creator Tool

{% stepper %}
{% step %}
#### Open the Creator Menu

In-game, use the command:

```
/aptdev
```

This opens the apartment developer menu.
{% endstep %}

{% step %}
#### Select Your Complex

1. Click **"Select Complex"**
2. Choose your complex from the list
3. The complex you configured in `shared/complexes/` will appear here

{% hint style="info" %}
**Can't see your complex?** Make sure it's registered in `shared/main.lua` and you restarted the resource.
{% endhint %}
{% endstep %}

{% step %}
#### Create a New Room

1. Click **"Create Room"**
2. Enter the room number (e.g., 101, 102, etc.)
3. The creator will switch to room setup mode

You'll now configure this room step-by-step.
{% endstep %}

{% step %}
#### Set Room Floor

1. Enter the floor number (e.g., 1 for first floor, 2 for second floor)
2. This is used for organization and display

Floor numbers don't have to match room numbers. Floor 1 can have rooms 101-110, Floor 2 can have rooms 201-210, etc.
{% endstep %}

{% step %}
#### Configure Doors

**For each door in the room:**

1. Stand at the door location
2. Click **"Add Door"**
3. The creator captures:
   * Door coordinates
   * Door model (from the object you're near)
   * Door heading

**For multi-door apartments:**

* Repeat this step for each door (front door, back door, etc.)
* Each door has independent lock states

{% hint style="success" %}
**Most rooms have 1 door.** Multi-door support is for apartments with multiple entrances.
{% endhint %}
{% endstep %}

{% step %}
#### Set Room Zone

The zone defines the walkable area inside the apartment.

**Box Zone (recommended for most MLOs):**

1. Click **"Create Box Zone"**
2. Stand in the center of the room
3. Enter the size (width, length, height)
4. The zone is created

**Poly Zone (for irregular shapes):**

1. Click **"Create Poly Zone"**
2. Walk around the room perimeter
3. Click **"Add Point"** at each corner
4. Click **"Finish Zone"** when done

{% hint style="info" %}
**Box zones are easier.** Only use poly zones if your room has an irregular shape.
{% endhint %}
{% endstep %}

{% step %}
#### Set Spawn Point

Where players spawn when they enter the apartment.

1. Stand where you want players to spawn
2. Look in the direction they should face
3. Click **"Set Spawn Point"**

The spawn point is saved with coordinates and heading.
{% endstep %}

{% step %}
#### Set Shell Origin (MLO Rooms Only)

**For MLO rooms (not shell props):**

1. Stand at the room entrance/door
2. Click **"Set Shell Origin"**

This sets the reference point for the room.

**For shell prop rooms:** Skip this step.

{% hint style="warning" %}
**What's the difference?**

* MLO = Built into the map file (most apartment buildings)
* Shell = Prop object you spawn with code

If your apartment building is a permanent map file, it's an MLO.
{% endhint %}
{% endstep %}

{% step %}
#### Save the Room

1. Click **"Save Room"**
2. The room configuration is written to your complex file
3. You'll see a confirmation message

The room is now saved in `shared/complexes/your_complex.lua` in the `rooms = {}` table.
{% endstep %}

{% step %}
#### Test the Room

1. Close the creator menu
2. Walk to the door you configured
3. You should see a door sprite (lock icon)
4. Press E to interact with the door

If everything works, the room is ready!
{% endstep %}
{% endstepper %}

***

## Creating More Rooms

Repeat the process for each room in your complex:

1. `/aptdev` → Select Complex → Create Room
2. Enter room number
3. Set floor, doors, zone, spawn point
4. Save

You can create as many rooms as you want. The script handles hundreds of rooms without performance issues.

***

## Developer Commands

| Command   | What It Does                |
| --------- | --------------------------- |
| `/aptdev` | Open apartment creator menu |

***

## Tips

### Room Numbering

Use a consistent numbering system: (most apartments have room no on mlo)

* Floor 1: Rooms 101-110
* Floor 2: Rooms 201-210
* Floor 3: Rooms 301-310

This makes management easier.

### Zone Size

Make zones slightly smaller than the actual room. This prevents overlap with hallways or other rooms.

### Multi-Floor Buildings

Configure all elevator locations first, then create rooms floor by floor. This keeps things organized.

### Testing

Test each room after creation:

1. Try opening/closing the door
2. Walk into the zone
3. Check that furniture bounds work
4. Verify spawn point is correct

***

## Troubleshooting

### Can't see door sprite?

Check that:

1. Door coordinates are correct
2. Door model exists in the game
3. You're close enough to the door (within 20 units)

### Zone not triggering?

Make sure:

1. Zone coordinates are correct
2. Zone size covers the room area
3. You saved the room properly

### `/aptdev` command not working?

Verify:

1. `Config.debug = true` in config.lua
2. Resource was restarted after enabling debug
3. You have admin permissions (if ACE permissions are configured)

***

## Disable Debug Mode (Production)

When you're done creating rooms, turn off debug mode:

```lua
Config.debug = false
```

Then restart:

This disables developer commands for security.

***

## What You Created

After creating rooms, your complex file looks like:

```lua
return {
    label = 'My Apartments',
    -- ... other config ...

    rooms = {
        [101] = {
            floor = 1,
            doors = {
                { coords = vec3(100.0, 200.0, 30.0), model = `v_ilev_ph_door01`, heading = 90.0 }
            },
            zone = {
                type = 'poly',
                points = {
                vec3(-826.558, -730.462, 44.370),
                vec3(-821.309, -730.310, 44.370),
                vec3(-821.205, -724.813, 44.370),
                vec3(-826.559, -724.773, 44.370)
            },
            spawnPoint = vec4(102.0, 205.0, 30.0, 180.0),
            shellOrigin = vec3(100.0, 200.0, 30.0)
        },
        [102] = {
            -- Next room...
        }
    }
}
```

All generated automatically by the creator tool. No manual coordinate editing needed.

***

## Need Help?

* Support: [Meteo Studios Discord](http://discord.meteofivem.net/)
