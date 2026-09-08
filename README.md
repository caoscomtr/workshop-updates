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

## Publishing a release

Releases are built by GitHub Actions from a pushed tag — nothing is uploaded by hand, and no personal
access token is stored anywhere. The workflow is [`.github/workflows/yayinla.yml`](.github/workflows/yayinla.yml).

```bash
# 1. build, then put the package where the workflow can reach it
python build/kur.py --release-url https://github.com/caoscomtr/workshop-updates/releases/download/vX.Y/Workshop_vX.Y_update.zip
cp .../Workshop_vX.Y_update.zip          payload/
cp .../guncelleme_kanali/surum.json      surum.json

# 2. commit on a release branch, tag it, and push ONLY the tag
git switch -c yayin-vX.Y
git add -f payload/ surum.json SURUM_NOTU_vX.Y.md
git commit -m "Workshop update channel vX.Y"
git tag vX.Y && git push origin refs/tags/vX.Y      # Actions builds the Release here

# 3. only after the Release is live, put surum.json on main
git switch main && git checkout vX.Y -- surum.json SURUM_NOTU_vX.Y.md
git commit -m "Workshop update channel vX.Y" && git push origin main
```

**The order matters.** `surum.json` on `main` is what every installed Workshop reads. If it named
`vX.Y` before the Release existed, every client would try to download a file that is not there yet.
Tags and branches are independent, so tagging first closes that window completely.

The job refuses to publish unless the asset's SHA-256 **and** size match what `surum.json` promises,
then downloads the published asset to confirm the bytes clients will receive are the right ones.
`payload/` is deliberately kept off `main` — packages belong in Releases; it is committed on the tag
only because that is how the file reaches the runner.

### Nexus Mods

The workflow can push to Nexus as well (official Upload API), but it stays switched off until two
things exist. Add them under *Settings → Secrets and variables → Actions*:

| | |
|---|---|
| secret `NEXUSMODS_API_KEY` | from <https://www.nexusmods.com/users/myaccount?tab=api> |
| variable `NEXUS_FILE_ID` | the file id on the mod's *Manage Files* page (“API Info”) |

Without them the step is skipped with a note and the release still succeeds. It uploads the **update**
package; the full installer (~126 MB) cannot travel through the repository at all, because git refuses
files over 100 MB — that one still goes up by hand.

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
