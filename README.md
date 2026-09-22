<div align="center">

# Magic Toolbox

**An all-in-one Jamf Pro admin suite.**

A native macOS app that puts fifteen Jamf Pro tools behind one window — clone objects between
instances, diff two computers, audit smart groups, hunt down profile conflicts, build PPPC and
system extension profiles from a dropped `.app`, and tear an instance down (with a backup) when
you're finished with it.

[mdmmagic.au](https://mdmmagic.au)

</div>

---

Most of these started life as separate apps. Magic Toolbox is the same work in one place: a home
screen of tools, a shared credential store, and a consistent connect → check permissions → scan →
act flow in every one of them.

Tools that write to Jamf (Clone, Wipe, Restore, Unused, and the profile builders' optional upload)
say so below. Everything else is read-only or runs entirely on your Mac.

---

## The tools

| Tool | What it does |
|---|---|
| **Clone** | Copies objects between two Jamf instances — categories, buildings, departments, sites, network segments, scripts, extension attributes, smart/static groups, policies, macOS and iOS profiles, Mac and mobile apps, restricted software. Previews dependencies before it runs, and creates or updates on the destination. **Writes** |
| **Compare** | Two modes. *Compare Computers* diffs the inventory, scoped policies and profiles of two machines in one instance. *Compare Instances* diffs up to four instances — groups, scripts, extension attributes, packages, policies and profiles — and exports a branded HTML report. |
| **Wipe** | Backs up an instance to a JSON manifest, then selectively deletes what you choose. Covers advanced searches, policies, profiles, restricted software, groups, scripts, EAs, apps, packages, categories, departments, buildings, prestages, API integrations and roles. Dependency blockers stop you deleting something still in use. **Writes (destructive)** |
| **Restore** | Reads a Wipe backup file and recreates the objects it contains, Classic and Pro API alike. **Writes** |
| **Profile Conflicts** | Pulls every macOS and iOS configuration profile, decodes the embedded mobileconfig payloads, and reports keys set to different values by more than one profile. Conflicts can be marked reviewed so they stay quiet on the next run. |
| **Smart Group Audit** | Audits computer and mobile smart groups for empty membership, stale criteria, over-complex criteria (configurable threshold), duplicate criteria, conflicting criteria and multi-hop nesting loops. Exports HTML or CSV. |
| **PPPC Analyser** | Drop an `.app` or `.pkg` and it works out which privacy permissions the app asks for, then builds the matching PPPC profile. Save as `.mobileconfig` or upload straight to Jamf. |
| **System Extensions** | Detects endpoint security, network and driver extensions in a dropped app and builds the approval profile with the right team IDs and bundle IDs. |
| **Web Content Filter** | Builds content filter `.mobileconfig` profiles, with known-vendor configurations pre-filled. |
| **Icons** | Lists every Self Service policy icon plus Self Service and enrolment branding icons, flags which are unused, and downloads them individually or as a zip. |
| **Downloader** | Bulk-downloads scripts, computer and mobile EAs, macOS and iOS profiles, and package binaries (via JCDS or the on-prem fallback), with an HTML report of what came down. |
| **Login Item Profiles** | Scans this Mac's launch agents, launch daemons and login items, then builds a managed login items profile allowing, denying or prompting on team ID, bundle ID or name. |
| **Notifications** | Builds notification permission profiles from a dropped app, with alert style, badges, sounds, lock screen and Notification Centre defaults set in Preferences. |
| **Unused** | Finds packages and scripts not referenced by any policy or patch policy, unscoped profiles, disabled policies, and smart groups with no criteria — then deletes the ones you tick. **Writes (destructive)** |
| **Inspector** | Takes apart a `.pkg` or `.app` locally: payload tree, pre/post-install scripts, receipts, architecture, signing, and a review tab that highlights the risky bits. No network access at all. |

---

## Requirements

- macOS 15.0 (Sequoia) or later
- A Jamf Pro instance, for the tools that connect to one
- A licence key — the first 72 hours after install are a free trial of everything

---

## Connecting to Jamf Pro

Every connecting tool takes the same credentials:

| Field | Notes |
|---|---|
| **Server URL** | `https://acme.jamfcloud.com`. A bare tenant name (`acme`) is expanded to `acme.jamfcloud.com` automatically, and a missing scheme becomes `https://`. |
| **Auth** | Either an **API client** (client ID + secret, recommended) or a **username and password**. |

Each tool runs a permission pre-flight before it does anything, listing the privileges it needs
against what your account actually has, so a missing *Update Policies* surfaces on the permissions
screen rather than halfway through a clone.

**Saved servers** — add instances once under *Saved Servers → Manage Servers* on the home screen and
pick them from any tool. The profile list lives in `UserDefaults`; passwords and client secrets go
to the login Keychain (`com.mdmmagic.MagicToolbox`), never to disk in plain text.

`API_Endpoints.txt` is the full map of which endpoint every tool touches, kept in sync with the code.

---

## Preferences

⌘, or *Preferences…* from the menu bar icon:

- **Appearance** — light, dark, or follow the system
- **Profile name prefixes** — per-tool prefix applied when saving or uploading generated profiles
- **Report theme and branding** — accent colour, organisation name and logo for exported HTML reports
- **Notification defaults** — values the Notifications tool pre-fills for each dropped app
- **Debug logging** — enable per tool; logs are held in memory only and cleared on quit, and are
  readable from the terminal icon in the title bar

---

## Output

Everything is written through a save panel — the app is sandboxed and has no access to your disk
beyond what you pick.

| Tool | Produces |
|---|---|
| Compare, Clone, Wipe, Unused, Downloader, Profile Conflicts, Smart Group Audit | Branded, self-contained HTML reports |
| Smart Group Audit | CSV as well |
| PPPC, System Extensions, Web Content Filter, Login Item Profiles, Notifications | `.mobileconfig` (or direct upload to Jamf) |
| Wipe | JSON backup manifest — written *before* anything is deleted |
| Icons, Downloader | Images, scripts, profiles, packages, zip archives |

---

## Repository layout

```
MagicToolbox/
├── MagicToolboxApp.swift        App entry, window chrome, menu bar extra
├── ContentView.swift            Home screen, AppTool enum, tool routing
├── Tools/<Tool>/                One folder per tool (View + ViewModel + services)
└── Shared/
    ├── Models/                  JamfCredentials, ServerProfile
    ├── Services/                JamfAPIClient, KeychainService, ServerStore,
    │                            LicenseService, DebugLogger, PKGAppExtractor
    └── Views/                   About, Preferences, Licence, DebugLog,
                                 CredentialsForm, ServerManager
cloudflare-worker/               Licence activation worker
ToolIcons/                       Marketing icons, one per tool
API_Endpoints.txt                Every Jamf endpoint the app calls, by tool
```

Each tool is self-contained: a SwiftUI view, an `ObservableObject` view model holding the step
machine (`credentials → permissions → scanning → results`), and whatever services it needs. Shared
work — auth, token refresh, privilege lookup, Classic and Pro API requests — lives in
`JamfAPIClient`.

---

## Building

```bash
open MagicToolbox.xcodeproj
```

| | |
|---|---|
| Scheme | `MagicToolbox` |
| Bundle ID | `au.mdmmagic.MagicToolbox` |
| Deployment target | macOS 15.0 |
| Swift | 5.0 |
| Team | `HFUN8K236G` |
| Entitlements | `MagicToolbox.entitlements` — sandbox, outbound network, user-selected and Downloads read/write, Keychain access group |

No package dependencies — SwiftUI, AppKit, CryptoKit and Security only.

---

## Licensing

Activation is handled by a Cloudflare Worker in `cloudflare-worker/`, backed by a KV namespace of
licence records.

**In the app.** Keys look like `MAGIC-XXXXXXXX-XXXXXXXX-XXXXXXXX` (hex). The app posts the key plus
the Mac's hardware serial as a machine ID; the worker binds the key to that machine on first
activation and returns an Ed25519-signed JWT valid for 25 hours. Only the public key ships in the
binary — verification is entirely local, so a token that is still cryptographically valid keeps the
app licensed without a round trip. Lose the network and there's a 72-hour grace window past token
expiry; an explicit server rejection revokes immediately. Key and token both live in the Keychain
under `au.mdmmagic.magictoolbox`.

**The worker.** Three POST endpoints — `/activate`, `/check`, `/deactivate` — plus `/health` for a
binding sanity check. Both the key and machine ID arrive as headers (`X-Licence-Key`,
`X-Machine-ID`).

```bash
cd cloudflare-worker
wrangler secret put PRIVATE_KEY_PEM     # Ed25519 private key, PKCS#8 PEM
wrangler deploy
```

The private key exists only as a worker secret. It must never end up in this repository or in the
app binary.

---

## A note on the destructive tools

**Wipe** and **Unused** delete objects from a live Jamf instance. Wipe always writes its backup
manifest before the first delete, and Restore will recreate from that file — but a restored object
is a *new* object with a new ID, so anything referencing the old ID (scoping, policy payloads,
prestage assignments) will need rebuilding. Test on a sandbox instance first.

---

<div align="center">

**MDM Magic** · [mdmmagic.au](https://mdmmagic.au)

</div>
