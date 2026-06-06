# Mosaic

**A desktop control panel for Conan Exiles (Enhanced) dedicated servers — built for mod developers and testers.**

Mosaic provisions, configures, and runs a Conan Exiles dedicated server from a single window. It fetches SteamCMD and the server for you, manages your Steam Workshop mods with named profiles, exposes the server settings in a clean editor, and gives you a live console, log tail, and RCON — so you can spin up a modded test server and iterate without hand-editing a single config file.

> Windows desktop app. Currently targets the live (Enhanced) Conan Exiles build.

## Features

- **One-click provisioning** — Point Mosaic at an empty folder and it downloads SteamCMD, installs the Conan Exiles dedicated server, and lays down the config files. No manual SteamCMD wrangling.
- **Mod profiles** — Group Workshop mods into named profiles (e.g. *Dev*, *Vanilla*, *Release*) and switch between them instantly; the modlist is regenerated automatically.
- **Automatic mod downloads** — Adds/updates Workshop mods via SteamCMD, retries any that don't land, and fetches missing mods before launch so you never start with a half-synced list.
- **Import / export** — Pull a mod list from a `modlist.txt`, an ID list, or Workshop URLs; export it back out to share.
- **Server settings editor** — The common knobs (General, Administration, Combat, PvP, Progression, Survival, Crafting, Building) grouped to mirror the in-game menu, with the full `.ini` surface reachable through a searchable Raw-files tab.
- **Live console & logs** — The server console is shown in-app via a live log tail (no extra console window), with parsed server stats.
- **RCON** — Send admin commands to a running server straight from the app.
- **Ports & connection** — Game / query / RCON ports, multihome, and passwords in one place.
- **Save management** — Wipe the savegame (backups preserved) for a clean test run.
- **Quality-of-life** — Open the server folder in Explorer, open configs in your editor, launch the game client, and see your public IP for sharing.

## Download & install

1. Grab the latest **`Mosaic_<version>_x64_en-US.msi`** from the [Releases](../../releases) page.
2. Run the installer (Windows 10/11, 64-bit).
3. Launch **Mosaic** from the Start menu.

## First run

1. **Set up a server** — On first launch, either point Mosaic at an existing Conan Exiles dedicated-server folder, or pick an empty folder and let it provision a fresh install (this pulls several GB via SteamCMD — give it time).
2. **Configure** — Set the server name, passwords, region, and ports on the Home tab.
3. **Add mods** — Paste Workshop IDs/URLs or import a `modlist.txt` into a profile; Mosaic downloads them for you.
4. **Start** — Hit Start, watch the live console, and once it reports ready, share your IP + port.
5. Launch Conan Exiles will launch the launcher of Conan Exiles to avoid conflicts with the dev kit running. 

> **Modded servers:** keep **BattlEye off** — Conan won't load mods with it enabled. Mosaic exposes this toggle under Administration → Anti-cheat.

## Requirements

- Windows 10 / 11 (64-bit)
- An internet connection and disk space for the dedicated-server download (handled via SteamCMD, which Mosaic fetches automatically)

## Status

Early release (`0.1.0`). Feedback and bug reports welcome on the dev Discord.

## License

[MIT](LICENSE)
