---
description: >-
  Replace the meteo- prefix on every meteo script with your own server prefix
  using the renamer tool.
icon: pen-to-square
---

# How to Rename Meteo Scripts

This guide walks you through replacing the `meteo-` prefix on every Meteo script (e.g. `meteo-inventory`, `meteo-phone`, `meteo-jobtablet`) with your own server prefix so it shows up nicely in the FiveM resource list.

You can do this **right after installing the server**, **after applying an update**, or **whenever you want to switch prefixes**. The script is fully reversible (you can always go back to `meteo-`).

***

{% hint style="danger" %}
**Only supported on Meteo Server V2.3.0 and above.** Make sure to update your server to V2.3.0 (or newer) before using the renamer. Older versions are not supported and we cannot provide support for them.
{% endhint %}

{% hint style="warning" %}
**Read before you continue:**

* This feature is still **experimental**.
* You should have at least **intermediate coding skills**.
* Be careful when applying updates - new scripts always ship under the original `meteo-` names, so you will need to run the renamer again after each update.
* **Do NOT run this on your live/main server while players are online.** Use a backup or a test server first.
{% endhint %}

***

## What You Need

* Your server-data folder (the one that contains `server.cfg`)
* The renamer tool: `tools/meteo-rename.bat` that ships in your release
* About 30 seconds

***

## Steps

### 1. Open the tools folder in meteo server folder

Inside the meteo server folder, open the `tools/` folder and find:

```
tools/
└── meteo-rename.bat
```

### 2. Double-click `meteo-rename.bat`

A console window opens. You will see:

```
 Meteo Server V2 - Rename

  Server-data folder path:
```

### 3. Paste your server-data folder path

This MUST be the folder that contains `server.cfg`.

Examples of correct paths:

```
C:\fivem\server-data
D:\FiveM\Servers\my-server\server-data
```

You can paste it with or without quotes - both work.

Press **Enter**.

The script verifies that `server.cfg` and `resources/` exist in that folder. If they do not, it shows an error and asks again.

{% hint style="info" %}
If you point it at the wrong folder (no `server.cfg`), it will NOT proceed. So you cannot accidentally rename something else.
{% endhint %}

### 4. Choose option `1` to apply a custom prefix

```
  1) Apply custom prefix
  2) Restore to meteo-
  3) Cancel

  Choose [1/2/3]: 1
```

Type `1` and press **Enter**.

### 5. Type your new prefix

```
  New prefix (1-8 letters/digits only):
```

Examples of valid prefixes:

| You type   | Folders become             |
| ---------- | -------------------------- |
| `myserver` | `myserver-inventory`, ...  |
| `lscity`   | `lscity-inventory`, ...    |
| `rp`       | `rp-inventory`, ...        |

**Rules:**

* 1 to 8 characters
* Letters and digits only (no spaces, no symbols, no underscore, no hyphen)
* The trailing `-` is added for you automatically

Press **Enter**.

### 6. Confirm

The script shows what it is about to do:

```
  ----------------------------------------------------
   Path:    C:\fivem\server-data
   Current: meteo-
   New:     myserver-
  ----------------------------------------------------

  Continue? [y/N]:
```

Type `y` and press **Enter**.

### 7. Wait for it to finish

You will see output like:

```
 Renaming folders...
    meteo-inventory -> myserver-inventory
    meteo-phone -> myserver-phone
    meteo-chatv2 -> myserver-chatv2
    ... (and so on for every meteo- script)
 Renamed: 70 folder(s)

 Updating rename.lua files...
 Updated: 65 file(s)

 Updating server.cfg...
 Backup: C:\fivem\server-data\server.cfg.backup

  Done!
```

Press any key to close.

***

## Verifying It Worked

### Check the folder names

Open `server-data\resources\` and confirm folders no longer start with `meteo-`. They should now start with your prefix (`myserver-`, etc).

### Check server.cfg

Open `server-data\server.cfg` and look for the `ensure` lines. They should now read:

```
ensure myserver-core
ensure myserver-chatv2
ensure myserver-inventory
...
```

(Originally these said `ensure meteo-core`, `ensure meteo-inventory`, etc.)

A backup is automatically saved as `server.cfg.backup` in the same folder.

### Start your server

Start FiveM as usual. All Meteo scripts should load under their new names. The FiveM resource list will show your prefix.

***

## Common Questions

### Will this break my server?

No. Everything is updated together: folder names, internal cross-references inside each script (`shared/rename.lua`), and the `ensure` lines in `server.cfg`. The scripts find each other through a single config value, so they all stay connected.

### What about `msv2-versioncheck`?

That one keeps its name on purpose. It does NOT have the `meteo-` prefix and the script intentionally skips it. Do not rename it manually.

### What about `ox_lib`, `ox_doorlocks`, etc?

Those are NOT touched. The renamer only changes folders that start with `meteo-` (or whatever your current prefix is). Third-party scripts keep their original names.

### Can I run it again after installing an update?

Yes. When we ship updates, new scripts come in with the `meteo-` prefix. Just run the tool again with the **same prefix you used last time** - it will detect any leftover `meteo-` scripts and convert them.

```
meteo-rename.bat  ->  Choose 1  ->  Type your prefix  ->  Continue
```

### Can I switch to a different prefix later?

Yes. Just run the tool and enter a different prefix. It will rename everything from your current prefix to the new one.

### How do I go back to `meteo-`?

Run the tool, choose option `2) Restore to meteo-`, confirm. Done.

### What if something goes wrong?

The tool always backs up `server.cfg` before editing it. The backup file is right next to it: `server.cfg.backup`. You can delete the broken one and rename the backup back to `server.cfg`.

For folders, just run the tool again with your previous prefix (or `--restore`) and it will revert them.

### Why does Windows show a warning when I open the .bat?

If you got the file from a download (Discord, Drive, browser), Windows may show "Windows protected your PC". Click **More info** -> **Run anyway**.

The script only renames folders and edits text files in the path you give it. It does not touch anything else and does not connect to the internet.

***

## Advanced (CLI mode)

If you prefer the command line:

```
meteo-rename.bat "C:\fivem\server-data" myserver
meteo-rename.bat "C:\fivem\server-data" --restore
```

Same behavior, no prompts.

***

{% hint style="success" %}
**Need help?** Open a ticket on our official Discord at <a href="https://discord.meteofivem.net" target="_blank">discord.meteofivem.net</a>. Our team is there to help every customer.
{% endhint %}
