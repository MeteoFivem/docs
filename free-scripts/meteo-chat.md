---
description: Free chat script with job chats, 3D text RP commands, auto messages and more.
icon: comments
---

# Meteo Chat

{% hint style="info" %}
Get this script for free from: <a href="https://meteo.tebex.io/" target="_blank">meteo-chat</a>
{% endhint %}

***

## Chat Features

* Press **T** to open the chat
* Chat comes with emoji support. Use **Left Alt** to enable mouse and use emojis and access settings menu
* Use `/clear` to clear the chats

### Chat Commands

* `/me action` - 3D text showing your action above character
* `/do action` - 3D text for describing environment/situation
* `/try action` - 3D text with random success/fail result
* `/ooc message` - out of character message

### Default Job Chat Channels

* `/police message` - police only chat (need police job)
* `/ems message` - ems only chat (need ambulance job)
* `/mechanic message` - mechanic only chat (need mechanic job)

## Installation Guide

{% stepper %}
{% step %}
**Remove the default chat**

Stop and remove the default `chat` resource from your server. Either delete the folder or comment out its `ensure` line in `server.cfg`.
{% endstep %}

{% step %}
**Install meteo-chat**

* Download the script from <a href="https://portal.cfx.re/" target="_blank">CFX Portal</a>
* Drop the `meteo-chat` folder into your resources (for example `[meteostudios]/meteo-chat`)
* Add `ensure meteo-chat` to your `server.cfg`

{% hint style="warning" %}
Make sure `ox_lib` is started **before** `meteo-chat` in your `server.cfg`, otherwise the script will throw errors on startup.
{% endhint %}
{% endstep %}

{% step %}
**Update existing `ensure chat` references**

If your `server.cfg` (or any other config) still has `ensure chat`, change it to `ensure meteo-chat` so nothing tries to start the old chat resource.
{% endstep %}

{% step %}
**Restart the server**

Start the server and press `T` in game to confirm the chat opens.
{% endstep %}
{% endstepper %}

***

## Configuration

All settings live in `shared/config.lua`.

### Welcome message

Shown to a player shortly after they spawn in.

```lua
Config.WelcomeMessage = {
    enabled = true,
    message = "Welcome to the Meteo Server! Press T to open chat and type / to see available commands.",
    delay = 2000, -- ms before the message is shown
}
```

### Auto messages

Rotating messages broadcast to everyone on a timer.

```lua
Config.AutoMessages = {
    enabled = true,
    interval = 30, -- minutes between messages
    messages = {
        "Don't Forget to join Meteo Discord!",
        "Have fun!",
    }
}
```

### Job chats

Adds a `/command` for each job that only members of that job can see.

```lua
Config.JobChats = {
    enabled = true,
    jobs = {
        { jobName = 'police',    command = 'police',   label = 'POLICE',   help = 'Send a message to all police officers' },
        { jobName = 'ambulance', command = 'ems',      label = 'EMS',      help = 'Send a message to all EMS members' },
        { jobName = 'mechanic',  command = 'mechanic', label = 'MECHANIC', help = 'Send a message to all mechanics' },
    }
}
```

`jobName` is the QBCore/QBox job, `command` is what players type (for example `/police hello`), `label` is the prefix shown in chat.

### 3D text display

Controls the floating 3D text shown above a player's head for RP commands.

```lua
Config.Display3D = {
    viewDistance = 15.0, -- distance to start showing the text
    maxDistance = 25.0,  -- distance to stop showing the text

    meDuration = 700,    -- /me
    doDuration = 700,    -- /do
    tryDuration = 700,   -- /try
    rollDuration = 1200, -- /roll
    sayDuration = 900,   -- /say
}
```

### IC speech (`/say`)

Proximity speech for text-based RP servers.

```lua
Config.Say = {
    proximity = 20.0,             -- meters
    display3D = true,             -- show speech above the speaker's head
    defaultOnPlainMessage = false, -- treat plain chat (no /command) as /say
}
```

Set `defaultOnPlainMessage = true` if you want typing in chat to behave like talking by default.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>.
{% endhint %}