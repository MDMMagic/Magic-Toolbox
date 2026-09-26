> [!WARNING]
> **Licence purchasing is not available at the moment, but will be in the near future.** If you would like a licence, email [info@mdmmagic.au](mailto:info@mdmmagic.au) to be notified once purchasing becomes available. In the meantime, every new install includes a 72-hour free trial with all features unlocked.

<div align="center">

# Magic Toolbox

**An all-in-one Jamf Pro admin suite.**

A native macOS app that puts eighteen Jamf Pro tools in one window. Clone objects between
servers, compare two computers or mobile devices, audit smart groups, accounts and certificates,
find profile conflicts, build PPPC, system extension, notification and login item profiles from a
dropped `.app`, and wipe a test server (with an encrypted backup) when you're finished with it.

[⬇️ Download the latest release](https://github.com/MDMMagic/Magic-Toolbox/releases/latest) · [📖 Documentation](https://github.com/MDMMagic/Magic-Toolbox/wiki) · [mdmmagic.au](https://mdmmagic.au)

</div>

---

Every tool follows the same flow: **connect → check permissions → scan → act**. Servers you save
once are available in every tool.

Tools that change Jamf Pro are marked below. Everything else is read-only or runs entirely on
your Mac.

---

## The tools

### Across Jamf Pro servers

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Clone](https://github.com/MDMMagic/Magic-Toolbox/wiki/Clone)** | Copies categories, buildings, departments, sites, network segments, scripts, extension attributes, smart and static groups, policies, macOS and iOS profiles, Mac and mobile apps, and restricted software from one server to one or more others. Copies missing dependencies, and asks before overwriting anything with the same name | ✏️ Yes (destinations) |
| **[Compare](https://github.com/MDMMagic/Magic-Toolbox/wiki/Compare)** | Three modes. *Compare Computers* shows the policies, groups and profiles two Macs have in common and where they differ. *Compare Mobile Devices* does the same for apps, groups and profiles on two iPhones or iPads. *Compare Instances* compares policies, groups, profiles, scripts, EAs and packages across 2–4 servers. Exports an HTML report | 👁️ Read-only |
| **[Wipe](https://github.com/MDMMagic/Magic-Toolbox/wiki/Wipe)** | Makes an encrypted backup of a DEV or TEST server, then deletes the objects you choose, in a safe order | 🗑️ Yes (deletes) |
| **[Restore](https://github.com/MDMMagic/Magic-Toolbox/wiki/Restore)** | Re-creates objects from a Wipe or Unused backup, in dependency order, on any server | ✏️ Yes (creates) |
| **[Disable](https://github.com/MDMMagic/Magic-Toolbox/wiki/Disable)** | Disables policies, Jamf Pro accounts and App Installers, and removes scope from profiles, restricted software and apps, without deleting anything | ✏️ Yes (disables) |

### Audit and health checks

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Profile Conflicts](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Conflicts)** | Finds macOS and iOS configuration profiles that manage the same payloads or keys on the same devices, taking exclusions into account. Conflicts can be marked reviewed | 👁️ Read-only |
| **[Smart Group Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Smart-Group-Audit)** | Checks computer and mobile smart groups for empty, overly complex, duplicate, contradictory and looping criteria. Exports HTML or CSV | 👁️ Read-only |
| **[Account Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Account-Audit)** | Lists Jamf Pro admin accounts, API roles and API clients, and flags broad-access clients and single-admin risk | 👁️ Read-only |
| **[Cert & Token Expiry](https://github.com/MDMMagic/Magic-Toolbox/wiki/Cert-and-Token-Expiry)** | Shows when ADE and VPP tokens expire, whether Jamf Pro has flagged the APNs push certificate as expiring, and whether an External CA is configured | 👁️ Read-only |
| **[Unused](https://github.com/MDMMagic/Magic-Toolbox/wiki/Unused)** | Finds unused packages, scripts, dock items and categories, unscoped profiles, apps and restricted software, disabled policies, empty smart groups and searches, and unlinked buildings, departments and network segments | 🗑️ Optional delete (encrypted backup first) |

### Profile builders

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[PPPC Analyser](https://github.com/MDMMagic/Magic-Toolbox/wiki/PPPC-Analyser)** | Works out which privacy (TCC) permissions an app asks for and builds the PPPC profile. Can also export a macOS 27+ AppSettings declaration | ⬆️ Optional upload |
| **[System Extensions](https://github.com/MDMMagic/Magic-Toolbox/wiki/System-Extensions)** | Finds endpoint security, network and driver extensions in an app and builds the approval profile with the right Team IDs and bundle IDs | ⬆️ Optional upload |
| **[Web Content Filter](https://github.com/MDMMagic/Magic-Toolbox/wiki/Web-Content-Filter)** | Builds content filter profiles, with known vendors' details filled in automatically | ⬆️ Optional upload |
| **[Notifications](https://github.com/MDMMagic/Magic-Toolbox/wiki/Notifications)** | Builds notification settings profiles for an app. Uploads with the category and scope you choose | ⬆️ Optional upload |
| **[Login Item Profiles](https://github.com/MDMMagic/Magic-Toolbox/wiki/Login-Item-Profiles)** | Scans this Mac's launch agents, launch daemons and login items, and walks you through building a Managed Login Items profile by Team ID, bundle ID or label. Uploads with the category and scope you choose | ⬆️ Optional upload |

### Content and packages

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Inspector](https://github.com/MDMMagic/Magic-Toolbox/wiki/Inspector)** | Looks inside a `.pkg` or `.app` without installing or running it: signing, entitlements, installed files, scripts, receipts, and a review that highlights risky patterns. No network access at all | 💻 Local only |
| **[Downloader](https://github.com/MDMMagic/Magic-Toolbox/wiki/Downloader)** | Previews and downloads scripts, computer and mobile EAs, and macOS and iOS profiles as ready-to-use files, with an HTML report | 👁️ Read-only |
| **[Icons](https://github.com/MDMMagic/Magic-Toolbox/wiki/Icons)** | Collects every Self Service policy icon, plus macOS and iOS Self Service and enrollment branding images, and turns any app's icon into a PNG for Self Service | ⬆️ Optional upload |

---

## Requirements

- macOS 15 Sequoia or later
- A Jamf Pro server, for the tools that connect to one
- A licence. Every tool can be tried free first: see [Licensing and Trial](https://github.com/MDMMagic/Magic-Toolbox/wiki/Licensing-and-Trial)

---

## Connecting to Jamf Pro

Every connecting tool takes the same details:

| Field | Notes |
|---|---|
| **Server URL** | `https://acme.jamfcloud.com`. A tenant name on its own (`acme`) is expanded to `acme.jamfcloud.com`, and `https://` is added if you leave it off |
| **Authentication** | An **API client** (client ID and secret, recommended) or a **username and password** |

Each tool checks your account's privileges before it does anything, so a missing *Update Policies*
shows up on the permissions screen rather than halfway through a clone. See
[Jamf API Permissions](https://github.com/MDMMagic/Magic-Toolbox/wiki/Jamf-API-Permissions) for
what each tool needs.

**Saved servers**: add servers once under *Saved Servers → Manage Servers…* on the home screen and
pick them from any tool. Passwords and client secrets are kept in the macOS Keychain, never on disk
in plain text.

---

## Preferences

Press ⌘, or choose *Preferences…* from the menu bar icon:

- **Appearance**: light, dark, or follow the system
- **Profile name prefixes**: a prefix for each profile builder, added when saving or uploading
- **Report theme and branding**: accent colour, organisation name and logo for exported HTML reports
- **Notification defaults**: the settings the Notifications tool starts with for each app
- **Debug logging**: turn on per tool. Logs are kept in memory only and cleared when you quit

---

## Output

Magic Toolbox is sandboxed, so everything is saved through a save panel. The app can't reach
anything on your disk you haven't picked.

| Tool | Produces |
|---|---|
| Clone, Compare, Wipe, Disable, Unused, Downloader, Profile Conflicts, Smart Group Audit, Account Audit, Cert & Token Expiry | Branded, self-contained HTML reports |
| Smart Group Audit | CSV as well |
| PPPC Analyser, System Extensions, Web Content Filter, Notifications, Login Item Profiles | `.mobileconfig` files, or a direct upload to Jamf Pro |
| PPPC Analyser | AppSettings declaration JSON (macOS 27+) |
| Wipe, Unused | A passphrase-encrypted backup, saved *before* anything is deleted |
| Icons, Downloader | Images, scripts, EAs, profiles and zip archives |

---

## A note on the tools that change Jamf Pro

**Wipe** and **Unused** delete objects from a live Jamf Pro server. Both save an encrypted backup
first, and Restore can re-create objects from it. But a restored object is a *new* object with a
new ID, so anything that referred to the old ID (scope, policy payloads, prestage assignments) may
need re-linking. **Clone** overwrites objects with the same name on the destination, and
**Disable** has no backup. Try them on a test server first.

---

<div align="center">

**MDM Magic** · [mdmmagic.au](https://mdmmagic.au)

</div>
