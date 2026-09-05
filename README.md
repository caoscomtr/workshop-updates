# Workshop — update channel

This repository is the update feed for **Workshop**, a fan-made modding tool for
*Assassin's Creed IV Black Flag Resynced*.

There is no application source here — only the few files the tool needs to find its updates:

| File | What it is |
|---|---|
| `surum.json` | Current version, the download address of the update package, its SHA-256 and size, and the short note shown on the Workshop's Dashboard |
| `LICENSE` | Terms for Workshop's own code |
| `SURUM_NOTU_*.md` | Notes for that release |
| **Releases** | `Workshop_vX.Y_update.zip` — the update package itself |

## How the update works

The Workshop reads `surum.json` when it starts. If a newer version exists, a banner appears on the
Dashboard; **nothing is downloaded or installed until you press "Update now"**.

Before anything is written the package is checked:

- it must come over `https`
- its SHA-256 must match the value in `surum.json`
- it may only contain scripts, interface files and data — a package carrying an executable
  (`.exe`, `.dll`, `.pyd`, `.bat`, …) or writing outside the allowed folders is refused
- the current files are backed up first, and a half-finished update is rolled back

The launcher, the bundled Python and the `tools` folder are never changed by an update.

Update packages carry only what actually changed since the last full release, so they are small.
Game imagery and the runtime stay in the full package.

## Full installer

New users install from Nexus Mods:
<https://www.nexusmods.com/assassinscreedblackflagresynced/mods/197>

## Licence and trademarks

Workshop's own code and interface are covered by [`LICENSE`](LICENSE) — free personal use;
redistribution by permission. Bundled third-party components keep their own licences, listed in
`THIRD-PARTY-NOTICES.txt` inside the package.

*Assassin's Creed IV Black Flag* is a trademark of Ubisoft Entertainment. This tool is an
unofficial, fan-made utility, not affiliated with or endorsed by Ubisoft. All game names, images
and other game content belong to Ubisoft.
