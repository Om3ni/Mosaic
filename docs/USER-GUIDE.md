# Mosaic — User Guide

Mosaic is a desktop control panel for running dedicated game servers. It installs
the server for you, keeps your mods organized, exposes every setting in a clean
editor, and gives you a live console, backups, scheduled restarts, and RCON — so
you never have to hand-edit a config file or babysit SteamCMD.

It currently manages two games:

- **Conan Exiles** (Enhanced / live build)
- **Project Zomboid** (Build 42 by default, Build 41 available)

You can add both and switch between them; only one server runs at a time.

This guide covers everything: first-time setup, a quick start for each game, and
then a reference for every tab and feature. If you're brand new, read
**The window at a glance** and the **Quick start** for your game, then dip into
the reference sections as you need them.

---

## The window at a glance

Mosaic has three fixed regions plus a set of tabs.

**Top bar (always visible)**

- **Left:** the Mosaic name and the active game + app version.
- **Middle:** the **game switcher** — shows the active game and its folder. Click
  it to switch to another added game, add a new one, or remove one. Switching is
  blocked while a server is running.
- **Right:** the server controls — **Start**, **Stop**, **Restart**, **Update** —
  and the **status pill**.

**The status pill** tells you what the server is doing at a glance:

| Pill | Meaning |
|------|---------|
| `STOPPED` | No server running. |
| `STARTING` | Launched; still booting (waiting for the "ready" marker in its log). |
| `RUNNING` | Up and ready. |
| `RESTART NEEDED` | Running, but you changed settings or mods — restart to apply them. |
| `DOWNLOADING` / `MODS x/total` | SteamCMD is fetching mods. |
| `RESTART 4:07` | A scheduled restart is armed and counting down. |

**Left sidebar (the tabs):** Home · Mods · Backups · Logs · RCON · Settings.

**Bottom strip:** your server folder path, and four capability dots that turn on
as things become ready — **Process** (server installed), **SteamCMD** (installed),
**RCON** (enabled), **Files** (config present).

---

## Installing a server

The first time you open Mosaic — or whenever it can't find a valid server at the
current folder — the **Install a dedicated server** window appears.

1. Choose an **Install folder** (type a path or click **Browse…**). Pick an empty
   folder; each game gets its own self-contained folder.
2. Click **Install server**. Mosaic downloads SteamCMD (if needed) and then the
   dedicated server. **This is several GB and only happens once** — the output
   streams live in the window. You can **Abort** if you need to stop.
3. When it finishes, the window closes and you land on the **Home** tab.

You can re-open this any time from **Home → Setup & paths → Set up a new server…**,
and you can point Mosaic at a server you already have from the same panel (see
[Setup & paths](#setup--paths)).

> **Which build gets installed?** Conan installs the live build. Project Zomboid
> installs **Build 42** (the current build) by default. You can change the build
> before or after installing — see [Build / branch](#build--branch).

---

## Managing multiple games

Use the **game switcher** in the top bar to work with more than one game:

- **Add a game** — pick it from the switcher; Mosaic creates a folder for it and
  drops you into its setup. Then install the server as above.
- **Switch** — select an added game. Everything (mods, settings, logs, backups)
  is per-game and swaps with it.
- **Remove** — removes it from the switcher. Its files are left on disk by default,
  so you can re-add it later.

Switching, adding, and removing are all blocked while a server is running — stop
it first.

---

## Quick start: Conan Exiles

1. **Install** the server (above).
2. **Home → Essentials:** set the **Server name** (what players see in the
   browser), a **Join password** if you want it private, **Max players**, and your
   gameplay basics (PvP, etc.).
3. **Home → Network & RCON:** set your **Game port** / **Query port** if the
   defaults (7777 / 27015) clash with anything, and — recommended — turn on
   **Enable RCON** and set an **RCON password** so you can run admin commands and
   get restart warnings.
4. **Mods (optional):** paste Workshop IDs or links into a profile (see
   [Mods](#mods)). Mosaic downloads them for you.
5. If you're running mods, turn **BattlEye off** under
   **Settings → Administration → Anti-cheat** — Conan won't load mods with it on.
6. **Start.** Watch the boot in the server console. When the pill reads `RUNNING`,
   share your **Public connect** address from the Server panel.

> **Launching the game to join your own server:** use **Launch Conan** on Home and
> point it at **`FuncomLauncher.exe`**, *not* the game exe. The launcher syncs your
> modlist and keeps your server visible in Steam's list.

---

## Quick start: Project Zomboid

1. **Install** the server (above). This installs **Build 42**.
2. **Start the server once, then Stop it.** Project Zomboid generates its settings
   files (the sandbox file) on first boot. Mosaic will tell you to do this if you
   try to edit gameplay settings too early.
3. **Home → Essentials:** set the **Server name** (public browser name), **Join
   password** (optional), **Max players**, and tune zombies/loot/world as you like.
4. **Administration → Access:** change the default admin account (it ships as
   **admin / admin**). Do this before exposing the server publicly.
5. **Home → Network & RCON:** defaults are 16261 (game) / 16262 (query). Set an
   **RCON password** — Project Zomboid enables RCON simply by having one, and
   Mosaic needs it for clean shutdowns, player counts, and restart warnings.
6. **Mods (optional):** paste Workshop IDs/links (see [Mods](#mods)). Mosaic
   downloads them and warns you if any mod's dependencies are missing.
7. **Start.** When the pill reads `RUNNING`, share your **Public connect** address.

> **Server dies instantly on Start?** Build 42's launch script demands 16 GB of
> RAM. On a smaller machine, lower **Settings → Administration → Performance →
> Java memory limit** (e.g. `8g`) and Start again. If the server exits during boot,
> Mosaic surfaces its actual error in a toast and the console instead of failing
> silently.
>
> **Build 41 vs 42:** a Build 42 client can't join a Build 41 server (and vice
> versa). Keep the [branch](#build--branch) matched to the client you play on.

---

## Reference

### Home

The Home tab is your dashboard. It has three parts.

**Left — quick settings**

- **Essentials:** the handful of settings most people change (server name,
  password, max players, and a few gameplay knobs). These are the same values as
  the full Settings tab, just curated. Edit and click **Save settings**.
- **Network & RCON:** game/query ports, multihome (bind IP — leave blank for all
  interfaces), and RCON (enable toggle, port, password). Ports and RCON take effect
  on the next **Start/Restart**. For Conan, RCON needs both the toggle **and** a
  password; for Project Zomboid, a password alone enables it.

Saving while the server is running offers a **Restart now** prompt, since these
changes only apply on (re)start.

**Right — Server panel**

- **Live status:** State, Uptime, Players, FPS, Map, and Active mod count. (Conan
  reports all of these from its log; Project Zomboid reports the player count over
  RCON when RCON is on, plus name/map/uptime.)
- **Connect info:** **Public connect** (your internet IP + port, for friends),
  **Local connect** (LAN), **Join password**, and **Admin password**. Each has a
  copy button.

**Right — Quick and Scheduled Actions**

- **Launch <game>** — starts the game client so you can join (Conan launches your
  chosen launcher exe; Project Zomboid launches through Steam).
- **Check for mod updates** — runs SteamCMD to update Workshop mods.
- **Broadcast a message** — sends a message to everyone in-game (needs RCON ready).
- **Restart warning 10 / 5 / 1 min** — one-click warning broadcasts.
- **Scheduled restarts & auto-check mods** — see [Automation](#automation).

### Mods

The Mods tab manages the mods for the **active profile**.

**Profiles** (the bar at the top) are named mod loadouts — e.g. *Vanilla*, *Dev*,
*Release*. Switch between them instantly; the server's modlist is repointed
immediately. Use **New**, **Duplicate**, **Rename**, **Delete**.

**Adding mods**

- Click **Add mods** and paste Workshop IDs or links (one or many, any separator).
  Mosaic extracts the IDs and adds them.
- **Conan only:** you can also add local **`.pak`** files (e.g. a Dev Kit build) —
  click **Browse local .pak…** or **drag-and-drop** `.pak` files onto the list.
  Project Zomboid is Workshop-only.

Added mods download automatically before the next Start, or immediately if you
click **Update** / **Check for mod updates**. Undownloaded mods are flagged **not
downloaded** until they arrive.

**Order matters.** Drag rows to reorder — load order is preserved for the server.

**Dependency warnings (Project Zomboid):** if a mod requires another mod that
isn't in your profile, an amber banner names the missing dependency and which mod
needs it — so you can add it before the server boots into a mod error.

### Settings

The full settings editor, grouped into tabs that mirror each game's own menu
(Conan: General, Administration, Combat, PvP, Progression, Survival, Crafting,
Building; Project Zomboid: General, Administration, Zombies, Loot, World, Time,
Survival).

- **Search** across all categories from the box at the top.
- **Hover or focus** any setting to see an explanation in the side panel.
- Edit, then **Save settings**. If the server is running, you'll be offered a
  restart to apply the changes.

**Raw files** (the last tab) is the escape hatch: it edits the actual config files
directly, for the long tail of keys the structured tabs don't surface. Pick a file,
use **Find in file…** to jump around, edit, and **Save**. Edit while the server is
**stopped** for reliable saves — a running server can overwrite these files when it
saves or exits.

> **Project Zomboid gameplay settings** live in the generated sandbox file, so you
> must **Start the server once** before you can edit them. Mosaic prompts you if
> you try too early.

### Backups

Point-in-time snapshots of your world, stored beside the server in a
`Mosaic-Backups` folder.

- **Capture backup** — name it and click Capture. **Stop the server first** — a
  live world can't be safely copied.
- **Restore** — copies a slot back over the live world. Mosaic **snapshots the
  current world first**, so a restore is itself reversible.
- **Delete** — removes a slot.

Each slot shows an integrity tag: **✓ verified** (databases passed a check),
**⚠ corrupt** (a database is damaged), or **no db** (nothing to check). A corrupt
slot, or one captured on a different game build, can still be restored but requires
an explicit confirm. A slot captured under a *different server name* is refused
outright, because its files wouldn't line up — restore it by setting the server
name back first.

Old automatic pre-restore snapshots are pruned for you (the newest few are kept).

### Logs

The in-app console, with two sources (toggle at the top):

- **SteamCMD** — output from installs and mod downloads/updates.
- **Server console** — a live tail of the running server's log. This is where you
  watch the boot sequence and any in-game server messages.

Starting or restarting the server jumps you here automatically so you can watch it
come up.

### RCON

A console for sending admin commands to the running server.

RCON is **ready** only when the server is running, RCON is enabled, and a password
is set. If it isn't ready, the tab tells you exactly what's missing and links you
to fix it.

Below the status is a **cheat sheet** of common commands for the active game —
click one to run it (or to pre-fill it if it needs you to type a name/message).
Examples:

- **Conan:** `ListPlayers`, `broadcast`, `saveworld`, `kick`, `ban`, `DoRestart`,
  `shutdown`. (Conan has no "promote to admin" RCON verb — log in with the Admin
  password and use the in-game **Make Me Admin** button.)
- **Project Zomboid:** `players`, `setaccesslevel` (promote an admin), `servermsg`
  (broadcast), `save`, `kickuser`, `banuser`, `addxp`, `quit`, and more.

Type any command in the box and press Enter to send it.

### Automation

Found at the bottom of **Home → Quick and Scheduled Actions**. Two independent jobs:

**Scheduled restarts**

- Turn on **Scheduled restarts** and click **Edit times & warnings**.
- Choose **Weekday / Weekend** lanes or **Every day** rows. Set up to **two times
  per day** (24-hour, server-local). Leave a slot blank to skip it.
- **Warnings** are broadcast to players before each restart. Each has a time
  (mm:ss before) and a message; `{t}` is replaced with the time remaining. The
  largest warning is the "lead" — the restart arms that far ahead and counts down
  in the status pill. You can **Abort** an armed restart.
- Restarts still fire without RCON, but players won't see the in-game warnings
  (RCON is needed to broadcast).

**Auto-check mods**

- Turn on **Auto-check mods** and set an interval (minutes). Mosaic re-validates
  your Workshop mods via SteamCMD in the background — **without taking the server
  down**.
- With **restart on change** enabled, a real mod update schedules a restart (using
  the same warning lead). A routine restart that lands right after a mod-update
  restart is skipped as redundant.

Click **Save automation** to persist changes. (Only one SteamCMD task runs at a
time, so an auto-check won't collide with a manual Update.)

---

## Setup & paths

The collapsible panel at the bottom of **Home**. This is where the plumbing lives.

- **Server root** — the folder your server lives in. **Apply** to point Mosaic at
  a different existing folder, or **Set up a new server…** to install a fresh one.
- **Server name (id)** *(Project Zomboid only)* — the internal id that names
  Project Zomboid's config, save, and database files (default `servertest`). This
  is **not** the public browser name (that's in Essentials). Changing it makes the
  server regenerate its files under the new name on the next Start; the old name's
  files stay on disk. Stop the server first. Letters, numbers, `_` and `-` only.
- **Build / branch** — see below.
- **Path checks** — green/red indicators for steamcmd, the server exe, Workshop
  content, config, and modlist, so you can see what's present.
- **Wipe world** — permanently deletes the savegame so a fresh world generates on
  the next Start. **Stopped only.** Your backups are preserved unless you tick the
  box to delete them too.

### Build / branch

Some games offer multiple builds ("branches"):

- **Conan:** Live (default) and TestLive.
- **Project Zomboid:** Unstable = **Build 42** (default) and Stable = **Build 41**.

Pick a build and click **Switch & reinstall** — Mosaic re-downloads the server on
that build (overwriting the install). **Your settings and saves are kept.** Stop
the server first. Mosaic checks Steam for the live branch list, so newly released
branches show up automatically.

> **Project Zomboid:** switching between Build 41 and 42 changes the world
> database format. If you're moving builds, wipe or back up first — restoring a
> backup across builds is guarded behind a confirm for this reason.

---

## Conan vs. Project Zomboid at a glance

| | **Conan Exiles** | **Project Zomboid** |
|---|---|---|
| Default build | Live | Build 42 (Unstable) |
| Server-name id | No (public name only) | Yes (`servertest`) — names its files |
| Mods | Workshop **and** local `.pak` | Workshop only |
| Default ports | 7777 / 27015 | 16261 / 16262 |
| Enable RCON | Toggle **+** password | Password alone |
| Launch client | Your launcher exe (`FuncomLauncher.exe`) | Through Steam |
| Clean shutdown | SaveWorld, then stop | RCON `quit` (save + graceful), then stop |
| Gameplay settings | Editable any time | Need one boot to generate first |
| Live stats | Players, FPS, map, uptime | Player count (via RCON), map, uptime |

---

## Troubleshooting

**The server says STARTING forever.** It's still booting (modded servers can take
several minutes). Open **Logs → Server console** to watch progress. If it never
reaches ready, check the console for errors.

**Project Zomboid server exits immediately on Start.** Almost always the 16 GB
heap that Build 42's launch script demands. Lower **Settings → Administration →
Performance → Java memory limit** (try `8g`) and Start again. Mosaic also shows the
server's own error message when it dies at boot.

**Conan won't load my mods.** Turn **BattlEye off** under
**Settings → Administration → Anti-cheat**, then restart.

**RCON won't connect.** RCON needs the server **running**, RCON **enabled**, and a
**password** set — then a **restart** to apply. The RCON tab tells you which piece
is missing. (Conan also needs the enable toggle on; Project Zomboid just needs the
password.)

**A mod shows "not downloaded."** Click **Update** (or **Check for mod updates**),
or just Start — Mosaic fetches missing mods before launch. Local `.pak` mods that
show missing mean the file isn't at that path anymore.

**Player warnings before restarts aren't showing in-game.** Warnings are broadcast
over RCON — enable RCON and set a password. Restarts still fire without it.

**I closed Mosaic but the server kept running.** That's by design — when you close
the window with a server up, Mosaic asks whether to stop it or leave it running.
"Leave running" keeps the server alive independently; reopen Mosaic to manage it
again.

**Switching games / branches / server name is blocked.** These are all stopped-only
operations. Stop the server first.

---

## Where your files live

Everything for a game lives under its **server root** folder.

- **Conan:** config and saves live inside the install
  (`ConanExilesDedicatedServer\ConanSandbox\Saved\…`). RCON settings are in
  `Game.ini` under `[RconPlugin]`; ports are passed on the command line.
- **Project Zomboid:** config, saves, and the world database live in a `pzdata`
  folder *beside* the install (Project Zomboid's cache directory). Its one server
  ini (`servertest.ini`), sandbox file, and spawn regions are all named after the
  server-name id.
- **Backups:** a `Mosaic-Backups` folder next to the server, so they travel with it.

You can open any of these from the app: **Setup & paths** shows the exact paths,
and the Raw files tab shows each config file's location.

---

*Mosaic is a Windows desktop app. One server runs at a time; everything in this
guide is per-game and follows whichever game is active in the switcher.*
