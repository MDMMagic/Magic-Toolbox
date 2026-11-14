# Magic Toolbox

**An all-in-one Jamf Pro admin suite for macOS.**

A native Mac app that puts 44 Jamf Pro tools in one window. Clone objects between servers, send
and schedule MDM commands, troubleshoot devices, audit smart groups, accounts, policies, patches
and certificates, find stale Macs and unused objects, check security and compliance readiness,
build and sign profiles from a dropped `.app`, and wipe a test server (with an encrypted backup)
when you're finished with it.

[⬇️ Download the latest release](https://github.com/MDMMagic/Magic-Toolbox/releases/latest) · [📖 Documentation](https://github.com/MDMMagic/Magic-Toolbox/wiki) · [mdmmagic.au](https://mdmmagic.au)

<img width="2032" height="1796" alt="Magic Toolbox home screen" src="https://github.com/user-attachments/assets/ce8190c6-5177-4eb3-8db5-833ca0d6d6b6" />

---

Every tool follows the same flow: **connect → check permissions → scan → act**. Servers you save
once are available in every tool, and you can pin the tools you use most to **Favourites** at the
top of the Home screen.

Tools that change Jamf Pro are marked below. Everything else is read-only or runs entirely on
your Mac.

---

## What's new in 1.1.0

- **11 new tools:** Broadcast Command, Redeploy, Webhook Manager, Stale Devices, Profile Drift,
  Policy Audit, Patch Compliance, Conditional Access, Category Audit, Enrolment Funnel and App
  Icon Fetcher.
- **Scheduled Commands** in Command, **Device History** in Device Logs, and **Device Certificates**
  in Cert & Token Expiry.
- **Policy Scope is now Policy Audit**, with a new Policy Failures tab. Configuration profiles and
  Entra ID mappings that list `Policy Scope` keep working.
- **Favourites**, a **Test** button for saved servers, many more MDM commands, security scores in
  Fleet Health, a preview mode in Clone, folder restores, and more.

See the [full list](https://github.com/MDMMagic/Magic-Toolbox/wiki#whats-new-in-120).

---

## The tools

### Jamf Pro Tools

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Clone](https://github.com/MDMMagic/Magic-Toolbox/wiki/Clone)** | Copies policies, profiles, groups, scripts, EAs, apps, restricted software and more from one server to one or more others. Copies missing dependencies, asks before overwriting anything with the same name (saving an encrypted backup first), and has a preview mode that changes nothing | ✏️ Yes (destinations) |
| **[Compare](https://github.com/MDMMagic/Magic-Toolbox/wiki/Compare)** | Compares two computers, two mobile devices, or 2–4 Jamf Pro servers, side by side | 👁️ Read-only |
| **[Wipe](https://github.com/MDMMagic/Magic-Toolbox/wiki/Wipe)** | Makes an encrypted backup of a DEV or TEST server, then deletes the objects you choose, in a safe order. Includes a dry run | 🗑️ Yes (deletes) |
| **[Restore](https://github.com/MDMMagic/Magic-Toolbox/wiki/Restore)** | Re-creates objects from a Wipe, Unused or Clone backup (or a whole folder of them), or writes them back over the existing objects | ✏️ Yes (creates or updates) |
| **[Disable](https://github.com/MDMMagic/Magic-Toolbox/wiki/Disable)** | Disables policies, accounts, apps and App Installers, and removes scope from profiles and restricted software, without deleting anything. Saves an encrypted undo backup first | ✏️ Yes (disables) |
| **[Create](https://github.com/MDMMagic/Magic-Toolbox/wiki/Create)** | Creates categories, policies, profiles, API roles and clients, restricted software, groups, scripts and package records from one guided form | ✏️ Yes (creates) |
| **[Command](https://github.com/MDMMagic/Magic-Toolbox/wiki/Command)** | Finds Macs or mobile devices by name or group and sends them MDM commands, now or at a scheduled time | ✏️ Yes (sends commands) |
| **[Broadcast Command](https://github.com/MDMMagic/Magic-Toolbox/wiki/Broadcast-Command)** | Sends one MDM command to devices you pick on several Jamf Pro servers at once | ✏️ Yes (sends commands) |
| **[Device Logs](https://github.com/MDMMagic/Magic-Toolbox/wiki/Device-Logs)** | Shows a device's policy logs, MDM commands, usage, audits and management history in one place | 👁️ Read-only |
| **[LAPS](https://github.com/MDMMagic/Magic-Toolbox/wiki/LAPS)** | Shows the LAPS passwords for a Mac's managed local admin accounts, and rotates them | 👁️ Read-only (✏️ optional rotate) |
| **[MDM Command Queue](https://github.com/MDMMagic/Magic-Toolbox/wiki/MDM-Command-Queue)** | Shows a Mac's, iPhone's or iPad's pending, failed and completed MDM commands | 👁️ Read-only |
| **[Redeploy](https://github.com/MDMMagic/Magic-Toolbox/wiki/Redeploy)** | Reinstalls the Jamf management framework on one or more Macs | ✏️ Yes (sends commands) |
| **[Webhook Manager](https://github.com/MDMMagic/Magic-Toolbox/wiki/Webhook-Manager)** | Lists webhooks, and turns them on or off or deletes them | ✏️ Yes (webhooks) |
| **[Self Service Descriptions](https://github.com/MDMMagic/Magic-Toolbox/wiki/Self-Service-Descriptions)** | Writes standardised Self Service descriptions from an app name, website or script | 💻 Local only |

### Audit & Health Check

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Profile Conflicts](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Conflicts)** | Finds configuration profiles that manage the same payloads or keys on the same devices | 👁️ Read-only |
| **[Smart Group Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Smart-Group-Audit)** | Checks smart groups for empty, overly complex, duplicate, contradictory and looping criteria | 👁️ Read-only |
| **[Account Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Account-Audit)** | Lists Jamf Pro admin accounts, API roles and API clients, and flags broad access, single-admin risk and tokens with no expiry | 👁️ Read-only |
| **[Cert & Token Expiry](https://github.com/MDMMagic/Magic-Toolbox/wiki/Cert-and-Token-Expiry)** | Shows when the APNs certificate, ADE and VPP tokens expire, whether an External CA is set up, and which certificates on your Macs are about to expire | 👁️ Read-only |
| **[Unused](https://github.com/MDMMagic/Magic-Toolbox/wiki/Unused)** | Finds unused packages, scripts, groups, extension attributes, categories and more across 17 categories | 🗑️ Optional delete (encrypted backup first) |
| **[Network Check](https://github.com/MDMMagic/Magic-Toolbox/wiki/Network-Check)** | Tests whether this Mac can reach the endpoints Jamf, Apple, Microsoft, Google and others need, including your own Jamf Pro server | 💻 Local only |
| **[Script Auditor](https://github.com/MDMMagic/Magic-Toolbox/wiki/Script-Auditor)** | Lists every script with the policies that use it, and finds orphaned scripts | 👁️ Read-only |
| **[Fleet Health](https://github.com/MDMMagic/Magic-Toolbox/wiki/Fleet-Health)** | Shows managed counts, check-in health, top macOS versions and security compliance scores | 👁️ Read-only |
| **[Extension Attributes](https://github.com/MDMMagic/Magic-Toolbox/wiki/Extension-Attributes)** | Lists computer EAs with the smart groups that use them, and finds orphaned ones | 👁️ Read-only |
| **[Self Service Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Self-Service-Audit)** | Finds Self Service policies that are disabled or have no description or icon | 👁️ Read-only |
| **[Stale Devices](https://github.com/MDMMagic/Magic-Toolbox/wiki/Stale-Devices)** | Finds Macs that haven't checked in within a number of days you choose | 👁️ Read-only |
| **[Profile Drift](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Drift)** | Finds profiles installed on few Macs or none, and profiles on Macs that are no longer in Jamf Pro | 👁️ Read-only |
| **[Policy Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Policy-Audit)** | Lists every policy scoped to a Mac, and shows how often a policy completes or fails across its Macs | 👁️ Read-only (✏️ optional remove from scope) |
| **[Patch Compliance](https://github.com/MDMMagic/Magic-Toolbox/wiki/Patch-Compliance)** | Shows each patch title's latest version and how many Macs are on it | 👁️ Read-only |
| **[Conditional Access](https://github.com/MDMMagic/Magic-Toolbox/wiki/Conditional-Access)** | Checks Macs against rules you set: OS version, inventory age, FileVault, Gatekeeper, SIP and firewall | 👁️ Read-only |
| **[Category Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Category-Audit)** | Finds unused categories, sites with no computers and policies with no scope | 👁️ Read-only |
| **[Pre-stage Audit](https://github.com/MDMMagic/Magic-Toolbox/wiki/Pre-stage-Audit)** | Lists Mac and mobile device PreStage enrolments, with defaults, authentication and assigned devices | 👁️ Read-only |
| **[Enrolment Funnel](https://github.com/MDMMagic/Magic-Toolbox/wiki/Enrolment-Funnel)** | Follows ADE devices from Apple Business or School Manager through to enrolment in Jamf Pro | 👁️ Read-only |

### Profile Builders

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[PPPC Analyser](https://github.com/MDMMagic/Magic-Toolbox/wiki/PPPC-Analyser)** | Works out which privacy (TCC) permissions an app needs and builds the PPPC profile. Can also export a macOS 27+ AppSettings declaration | ⬆️ Optional upload |
| **[System Extensions](https://github.com/MDMMagic/Magic-Toolbox/wiki/System-Extensions)** | Finds endpoint security, network and driver extensions in an app and builds the approval profile | ⬆️ Optional upload |
| **[Web Content Filter](https://github.com/MDMMagic/Magic-Toolbox/wiki/Web-Content-Filter)** | Builds content filter profiles, with known vendors' details filled in automatically | ⬆️ Optional upload |
| **[Notifications](https://github.com/MDMMagic/Magic-Toolbox/wiki/Notifications)** | Builds notification settings profiles for an app | ⬆️ Optional upload |
| **[Login Item Profiles](https://github.com/MDMMagic/Magic-Toolbox/wiki/Login-Item-Profiles)** | Builds Managed Login Items (background task) profiles from this Mac's launch agents, daemons and login items | ⬆️ Optional upload |
| **[Profile Signer](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Signer)** | Signs `.mobileconfig` profiles and `.pkg` installers with a certificate from your keychain | 💻 Local only |
| **[Profile Unsigner](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Unsigner)** | Removes the signature from `.mobileconfig` profiles and `.pkg` installers | 💻 Local only |
| **[Profile Inspector](https://github.com/MDMMagic/Magic-Toolbox/wiki/Profile-Inspector)** | Shows every payload and setting in a `.mobileconfig` file | 💻 Local only |

### Content & Packages

| Tool | What it does | Changes Jamf? |
|---|---|---|
| **[Inspector](https://github.com/MDMMagic/Magic-Toolbox/wiki/Inspector)** | Looks inside a `.pkg` or `.app` without installing or running it: verified signatures, entitlements, files, scripts and a safety review | 💻 Local only |
| **[Downloader](https://github.com/MDMMagic/Magic-Toolbox/wiki/Downloader)** | Downloads scripts, extension attributes and configuration profiles from Jamf Pro as ready-to-use files | 👁️ Read-only |
| **[Icons](https://github.com/MDMMagic/Magic-Toolbox/wiki/Icons)** | Collects every Self Service icon and branding image, and turns any app's icon into a PNG for Self Service | ⬆️ Optional upload |
| **[App Icon Fetcher](https://github.com/MDMMagic/Magic-Toolbox/wiki/App-Icon-Fetcher)** | Finds an app's icon on the App Store or Wikipedia and saves it as a PNG | ⬆️ Optional upload |

---

## Requirements

- macOS 26 Tahoe or later
- A Jamf Pro server, for the tools that connect to one
- A licence. Every tool can be tried free for 72 hours first: see [Licensing and Trial](https://github.com/MDMMagic/Magic-Toolbox/wiki/Licensing-and-Trial)

---

## Connecting to Jamf Pro

Every connecting tool takes the same details:

| Field | Notes |
|---|---|
| **Server URL** | `https://acme.jamfcloud.com`. A tenant name on its own (`acme`) is expanded to `acme.jamfcloud.com`, and `https://` is added if you leave it off. On-premises servers work too |
| **Authentication** | An **API client** (client ID and secret, recommended) or a **username and password** |

Each tool checks your account's privileges before it does anything, so a missing *Update Policies*
shows up on the permissions screen rather than halfway through a clone. See
[Jamf API Permissions](https://github.com/MDMMagic/Magic-Toolbox/wiki/Jamf-API-Permissions) for
what each tool needs.

**Saved servers**: add servers once under *Saved Servers → Manage Servers…* on the Home screen,
check them with **Test**, and pick them from any tool. Passwords and client secrets are kept in the
macOS Keychain, never on disk in plain text.

---

## Deploying to your organisation

IT can configure Magic Toolbox for every Mac with a configuration profile: activate a licence,
choose which tools people see, require a PIN for risky tools, pre-fill your Jamf Pro server, brand
reports and add app shortcuts. With [Entra ID](https://github.com/MDMMagic/Magic-Toolbox/wiki/Entra-ID)
sign-in, people see only the tools their groups allow. See
[Managed Preferences](https://github.com/MDMMagic/Magic-Toolbox/wiki/Managed-Preferences).

---

## Preferences

Press ⌘, or choose *Preferences…* from the menu bar icon:

- **Appearance**: light, dark, or follow the system
- **Profile name prefixes**: a prefix for each profile builder, added when saving or uploading
- **Profile signing certificate**: the identity Profile Signer uses
- **Report theme and branding**: any accent colour, plus your organisation's name and logo, for exported HTML reports
- **Custom applications**: shortcuts to other apps on the Home screen
- **Tool Lock**: require a PIN before chosen tools open
- **Debug logging**: turn on per tool. Logs are kept in memory only and cleared when you quit

---

## Output

Magic Toolbox is sandboxed, so everything is saved through a save panel. The app can't reach
anything on your disk you haven't picked.

| Output | From |
|---|---|
| Branded, self-contained HTML reports | Most audit tools, plus Clone, Compare, Wipe, Disable, Unused, Downloader and Network Check |
| CSV | Smart Group Audit, Script Auditor, Pre-stage Audit, Stale Devices and Device Logs, among others |
| `.mobileconfig` files, or a direct upload to Jamf Pro | PPPC Analyser, System Extensions, Web Content Filter, Notifications and Login Item Profiles |
| AppSettings declaration JSON (macOS 27+) | PPPC Analyser |
| A passphrase-encrypted backup, saved *before* anything is deleted, overwritten or disabled | Wipe, Unused, Clone and Disable |
| Images, scripts, EAs, profiles and zip archives | Icons, App Icon Fetcher and Downloader |

---

## A note on the tools that change Jamf Pro

**Wipe** and **Unused** delete objects from a live Jamf Pro server. Both save an encrypted backup
first, and Restore can re-create objects from it. But a restored object is a *new* object with a
new ID, so anything that referred to the old ID (scope, policy payloads, PreStage assignments) may
need re-linking. **Clone** overwrites objects with the same name on the destination, after saving
an encrypted backup that Restore can write back; use its **Preview only** mode to see what would
change first. **Disable** saves an encrypted undo backup, and its **Undo from backup…** button puts
the original state and scope back. **Command**, **Broadcast Command** and **Redeploy** send MDM
commands to real devices, including lock and wipe. Try them on a test server first.

---

<div align="center">

**MDM Magic** · [mdmmagic.au](https://mdmmagic.au)

</div>
