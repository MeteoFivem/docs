---
description: >-
  These Meteo Phone commands help you manage phones and SIM cards on your
  server. All commands require admin permissions.
---

# Useful Commands

### Phone Commands

#### `/getphone [serial]`

**Give a phone to a player**

* **Usage:** `/getphone Ifruit_583686`
* **Parameter:**
  * `serial` - The unique serial number for the phone
* **What it does:** Gives you a phone with the specified serial number

**Example:**

```
/getphone Ifruit_583686
```

***

#### `/resetphone [serial]`

**Reset all data on a phone**

* **Usage:** `/resetphone Ifruit_583686`
* **Parameter:**
  * `serial` - The phone's serial number
* **What it does:** Deletes all data from the phone (notes, emails, photos, settings, etc.) but keeps the phone item

**Example:**

```
/resetphone Ifruit_583686
```

***

#### `/deletephone [serial]`

**Permanently delete a phone and all its data**

* **Usage:** `/deletephone Ifruit_583686`
* **Parameter:**
  * `serial` - The phone's serial number
* **What it does:** Completely removes the phone and all its data from the database

**Example:**

```
/deletephone Ifruit_583686
```

***

### SIM Card Commands

#### `/getsim [number]` (optional)

**Give a SIM card to a player**

* **Usage:** `/getsim` or `/getsim 555-123-4567`
* **Parameter:**
  * `number` (optional) - Custom phone number for the SIM
* **What it does:** Gives you a SIM card. If no number is provided, it generates a random one automatically (format: XXX-XXX-XXXX)

**Examples:**

```
/getsim
/getsim 555-123-4567
```

***

#### `/resetsim [number]`

**Reset all data on a SIM card**

* **Usage:** `/resetsim 555-123-4567`
* **Parameter:**
  * `number` - The phone number on the SIM card
* **What it does:** Deletes all data linked to that phone number (contacts, messages, calls, etc.) but keeps the SIM card item

**Example:**

```
/resetsim 555-123-4567
```

***

#### `/deletesim [number]`

**Permanently delete a SIM card and all its data**

* **Usage:** `/deletesim 555-123-4567`
* **Parameter:**
  * `number` - The phone number on the SIM card
* **What it does:** Completely removes the SIM card and all its data from the database

**Example:**

```
/deletesim 555-123-4567
```

***

### Finding Phone Serial Numbers

**If a player loses their phone and needs a replacement:**

1. Player goes to the phone shop
2. Player can **copy the serial number** from the shop interface
3. Admin uses `/getphone [serial]` to give them a new phone with the same serial
4. Player's data will be restored automatically

***

### Quick Reference Table

| Command                 | Purpose                 | Example                      |
| ----------------------- | ----------------------- | ---------------------------- |
| `/getphone [serial]`    | Give phone              | `/getphone Ifruit_583686`    |
| `/getsim [number]`      | Give SIM card           | `/getsim 555-123-4567`       |
| `/resetphone [serial]`  | Clear phone data        | `/resetphone Ifruit_583686`  |
| `/resetsim [number]`    | Clear SIM data          | `/resetsim 555-123-4567`     |
| `/deletephone [serial]` | Delete phone completely | `/deletephone Ifruit_583686` |
| `/deletesim [number]`   | Delete SIM completely   | `/deletesim 555-123-4567`    |
