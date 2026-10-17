---
description: >-
  Every meteo-dialogue export with a simple example - opening NPC dialogues,
  chained steps, ped targets and spawning dialogue peds.
icon: code
---

# Exports

Use the meteo dialogue in your own scripts, so your NPCs talk the same way as every other NPC in the package.

{% hint style="warning" %}
All meteo-dialogue exports are **client** side only.
{% endhint %}

***

## Opening a Dialogue

### OpenDialogue(data, targetPed)

Opens a dialogue. Pass a ped to focus the camera on it and play the greeting voice line.

```lua
exports['meteo-dialogue']:OpenDialogue(data, targetPed)
```

* `data` - the dialogue table (see the format below)
* `targetPed` - optional, the ped entity to focus the camera on

### Dialogue Format

```lua
{
    name = 'Benny',                          -- NPC name
    role = 'Mechanic',                       -- optional, line under the name
    icon = 'wrench',                         -- optional, NPC icon
    text = 'Engine making noise?',           -- what the NPC says
    greeting = 'GENERIC_HOWS_IT_GOING',      -- optional, voice line on open (false = silent)
    options = {
        {
            title = 'Fix my car',            -- required
            description = 'Sultan RS',       -- optional, small line under the title
            icon = 'wrench',                 -- optional
            tag = '$450',                    -- optional, pill on the right
            image = 'https://.../car.png',   -- optional, big preview shown on hover
            thumb = 'nui://inv/water.png',   -- optional, small picture in the row itself
            tone = 'success',                -- optional: success, danger, warning, info, neutral
            disabled = false,                -- optional, greyed out and not clickable
            back = false,                    -- optional, returns to the previous step
            onSelect = function() end,       -- optional, runs when picked
        },
    },
}
```

* Options with no `onSelect` (like "Leave") close the dialogue and show a grey icon
* `image` shows a big preview card above the option list while the player hovers that option. Any URL works, including `nui://resource/path.png` for images inside another resource. It is scaled to fit, never cropped, up to 200px tall
* `thumb` puts a small square picture in the row itself, where the icon would go. Use it for **items**, with the url `nui://<inventory>/web/images/<item>.png`. If the picture fails to load, the option's `icon` is shown instead
* If `options` is empty, a single "Leave" option is shown
* Players can press `1`-`9` to pick, `Backspace` to go back and `ESC` to leave
* When a `targetPed` is passed, the NPC says a greeting on open. It plays once per conversation, not on chained steps. Common lines are `GENERIC_HI`, `GENERIC_HOWS_IT_GOING`, `GENERIC_THANKS` and `GENERIC_BYE`
* The trail of picked options (for example `Fix my car › Pay cash`) is shown next to the NPC name

### Icons

Any <a href="https://lucide.dev/icons" target="_blank">Lucide</a> icon name works, like `wrench`, `shopping-bag`, `credit-card` or `map-pin`.

The old names still work too: `chat`, `trade`, `info`, `work`, `exit`, `money`, `cigarette`, `location`, `craft`, `shop`, `key`, `garage`, `arrow_back`, `payments`, `restaurant` and `inventory_2`.

### Example

```lua
exports['meteo-dialogue']:OpenDialogue({
    name = 'Bob',
    role = 'Mechanic',
    icon = 'wrench',
    text = 'Need your car fixed? I can help.',
    options = {
        {
            title = 'Repair Vehicle',
            icon = 'wrench',
            tag = '$450',
            tone = 'success',
            onSelect = function()
                -- repair logic
            end,
        },
        { title = 'Nevermind', icon = 'x' },
    },
}, somePedEntity)
```

***

## Chained Dialogues

Call `OpenDialogue` inside an `onSelect` to move to the next step. The camera and focus stay active, and the new step slides in.

If `onSelect` does not open a new dialogue, everything closes once it finishes. `onSelect` runs in a thread, so `Wait()` and `lib.callback.await` are fine - the options dim while it runs.

Use `back = true` on an option (or `Backspace`) to return to the previous step. Opening an earlier step again yourself also rewinds the trail.

```lua
local function OpenMainMenu()
    exports['meteo-dialogue']:OpenDialogue({
        name = 'The Dealer',
        text = 'What are you looking for?',
        options = {
            {
                title = 'Buy Weapons',
                icon = 'gavel',
                onSelect = function()
                    exports['meteo-dialogue']:OpenDialogue({
                        name = 'The Dealer',
                        text = 'Here is what I have today.',
                        options = {
                            { title = 'Pistol', icon = 'crosshair', tag = '$500', tone = 'success', onSelect = function()
                                -- purchase logic
                            end },
                            { title = 'Back', icon = 'arrow-left', back = true },
                        },
                    }, myPed)
                end,
            },
            { title = 'Leave', icon = 'x' },
        },
    }, myPed)
end
```

***

## Old Format (v1)

The v1 array with `side` still works, so existing scripts do not need changes:

```lua
exports['meteo-dialogue']:OpenDialogue({
    { title = 'Bob', description = 'Need your car fixed?', icon = 'chat', side = 'right', disabled = true },
    { title = 'Repair Vehicle', description = 'Fix up my ride.', icon = 'craft', side = 'left', onSelect = function() end },
    { title = 'Nevermind', icon = 'exit', side = 'left' },
}, somePedEntity)
```

The first `right` entry becomes the NPC name and icon, and all `right` descriptions become the NPC text. `left` entries become the options.

***

## Closing and Checking

### CloseDialogue()

Closes the open dialogue.

```lua
exports['meteo-dialogue']:CloseDialogue()
```

### IsDialogueOpen()

Returns `true` while a dialogue is open.

```lua
local isOpen = exports['meteo-dialogue']:IsDialogueOpen()
```

***

## Ped Targets

### AddDialogueTarget(ped, data, label, icon, distance, canInteract)

Adds a target option to a ped that opens a dialogue. Needs ox\_target.

```lua
exports['meteo-dialogue']:AddDialogueTarget(ped, data, 'Talk', 'fas fa-comments', 2.0, function()
    return true
end)
```

* `ped` - ped entity handle
* `data` - dialogue table (same format as `OpenDialogue`)
* `label` - optional, target label, default `'Talk'`
* `icon` - optional, FontAwesome icon, default `'fas fa-comments'`
* `distance` - optional, interaction distance, default `2.0`
* `canInteract` - optional, function that returns `true` or `false`

### RemoveDialogueTarget(ped)

Removes the dialogue target from a ped.

```lua
exports['meteo-dialogue']:RemoveDialogueTarget(ped)
```

***

## Dialogue Peds

### SpawnDialoguePed(model, coords, scenario)

Spawns an NPC to talk to. The ped is frozen, invincible and ignores events. Returns the ped handle, or `nil` if the model did not load.

```lua
local ped = exports['meteo-dialogue']:SpawnDialoguePed('a_m_y_business_02', vector4(-268.5, -957.8, 31.2, 205.0), 'WORLD_HUMAN_STAND_IMPATIENT')
```

* `model` - model name or hash
* `coords` - `vector4(x, y, z, heading)`
* `scenario` - optional, a scenario to play

### DeleteDialoguePed(ped)

Removes the target and deletes the ped.

```lua
exports['meteo-dialogue']:DeleteDialoguePed(ped)
```

***

## Full Example

Spawn an NPC, give it a target and open a dialogue with a chained step.

```lua
local ped = exports['meteo-dialogue']:SpawnDialoguePed('s_m_y_xmech_02', vector4(-211.5, -1324.2, 30.9, 90.0))

exports['meteo-dialogue']:AddDialogueTarget(ped, {
    name = 'Benny',
    role = 'Mechanic',
    icon = 'wrench',
    text = 'Engine making noise?',
    options = {
        {
            title = 'Fix my car',
            icon = 'wrench',
            tag = '$450',
            onSelect = function()
                exports['meteo-dialogue']:OpenDialogue({
                    name = 'Benny',
                    text = 'How do you want to pay?',
                    options = {
                        { title = 'Pay cash', icon = 'banknote', onSelect = function()
                            -- payment logic
                        end },
                        { title = 'Back', icon = 'arrow-left', back = true },
                    },
                }, ped)
            end,
        },
        { title = 'Leave', icon = 'x' },
    },
})

AddEventHandler('onResourceStop', function(resource)
    if resource ~= GetCurrentResourceName() then return end
    exports['meteo-dialogue']:DeleteDialoguePed(ped)
end)
```
