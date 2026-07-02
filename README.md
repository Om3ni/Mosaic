# Mosaic

**A desktop control panel for dedicated game servers — install, configure, mod, and run them from a single window.**

Mosaic provisions, configures, and runs a dedicated server without making you
touch a config file or wrangle SteamCMD by hand. It fetches SteamCMD and the
server for you, manages your Steam Workshop mods with named profiles, exposes the
server settings in a clean editor, and gives you a live console, backups,
scheduled restarts, and RCON.

It currently manages two games, and you can add both and switch between them:

- **Conan Exiles** (Enhanced / live build)
- **Project Zomboid** (Build 42 by default, Build 41 available)

> Windows desktop app. One server runs at a time.

## 📖 User guide

New here? The **[User Guide](docs/USER-GUIDE.md)** is a complete, plain-language
walkthrough: first-time setup, a quick start for each game, and a reference for
every tab and feature. Start there.

## Features

- **One-click provisioning** — Point Mosaic at an empty folder and it downloads
  SteamCMD, installs the dedicated server, and lays down the config. No manual
  SteamCMD wrangling.
- **Multi-game** — Add Conan Exiles and Project Zomboid side by side and switch
  between them; mods, settings, logs, and backups are all per-game.
- **Mod profiles** — Group Workshop mods into named profiles (e.g. *Dev*,
  *Vanilla*, *Release*) and switch instantly; the modlist is regenerated
  automatically. Conan also accepts local Dev Kit `.pak` files.
- **Automatic mod downloads** — Adds/updates Workshop mods via SteamCMD, retries
  any that don't land, and fetches missing mods before launch. For Project
  Zomboid, warns you when a mod's dependencies are missing.
- **Import / export** — Pull a mod list from a `modlist.txt`, an ID list, or
  Workshop URLs; export it back out to share.
- **Server settings editor** — The common knobs grouped to mirror each game's
  in-game menu, with the full config surface reachable through a searchable
  Raw-files editor.
- **Safe shutdowns** — Stop/Restart save the world and shut the server down
  cleanly (Project Zomboid gets a graceful RCON quit; a hard kill is only ever a
  last resort), so a restart can't corrupt the world mid-write.
- **Backups** — Capture named snapshots of your world, restore them (the current
  world is snapshotted first, so a restore is reversible), with database integrity
  checks and guards against restoring onto the wrong server or build.
- **Scheduled restarts & auto-updates** — Restart on a weekday/weekend or per-day
  schedule with in-game warning broadcasts, and optionally auto-check Workshop
  mods and restart when one actually changes.
- **Live console & logs** — The server console is shown in-app via a live log tail
  (no extra console window), with parsed server stats.
- **RCON** — Send admin commands to a running server, with a per-game cheat sheet.
- **Ports & connection** — Game / query / RCON ports, multihome, and passwords in
  one place, plus your public IP for sharing.

## Download & install

1. Grab the latest **`Mosaic_<version>_x64_en-US.msi`** from the [Releases](../../releases) page.
2. Run the installer (Windows 10/11, 64-bit).
3. Launch **Mosaic** from the Start menu.

## First run

1. **Install a server** — On first launch, point Mosaic at an existing
   dedicated-server folder, or pick an empty folder and let it provision a fresh
   install (this pulls several GB via SteamCMD — give it time).
2. **Configure** — Set the server name, passwords, and ports on the Home tab.
3. **Add mods** — Paste Workshop IDs/URLs or import a `modlist.txt` into a profile;
   Mosaic downloads them for you.
4. **Start** — Hit Start, watch the live console, and once it reports ready, share
   your public IP + port.

See the **[User Guide](docs/USER-GUIDE.md)** for the full walkthrough and a quick
start tailored to each game.

**Game-specific notes:**

- **Conan (modded):** keep **BattlEye off** (Administration → Anti-cheat) — Conan
  won't load mods with it enabled. To join your own server, launch through
  `FuncomLauncher.exe`, not the game exe.
- **Project Zomboid:** change the default **admin / admin** account (Administration
  → Access) before going public. If the server dies instantly on Start, lower the
  **Java memory limit** (Administration → Performance) — Build 42 demands 16 GB by
  default. A Build 42 client can't join a Build 41 server.

## Requirements

- Windows 10 / 11 (64-bit)
- An internet connection and disk space for the dedicated-server download (handled
  via SteamCMD, which Mosaic fetches automatically)

## Status

Stable release (`1.0.0`). Feedback and bug reports welcome on the dev Discord.

## License

[MIT](LICENSE)
