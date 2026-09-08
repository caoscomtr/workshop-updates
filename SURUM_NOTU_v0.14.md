# Workshop v0.14

_2026-09-08_

Installing a mod is now two steps. Drop a .zip, a .rar, a folder, a ready-made .forge patch or a pile of loose textures onto the ADD A MOD page, read the one line that says what it changes in plain words - "Changes Edward Kenway's Robes (dress, hood, tunic)" - and press INSTALL. No slot numbers, no material ids, no percentages: those moved behind Show details for the people who want them. Everything you install is listed underneath with a Remove button, and removing one mod leaves the others alone. Before it writes anything the app warns you if a mod you already have changes the same part of the game, and says whether the two can live together or would have to come out together. If any part of an install fails, everything that mod had already written is put back and the app tells you the archive is the size it was before - measured in bytes, not promised. THE ARCHIVE EXPLORER: a new tab opens all 157 game archives and 2,165,452 entries by name, exports any of them and puts them back. If an entry is one the game no longer reads - because a later patch archive overrides it - the app now says so instead of writing a change that would never show up. UPDATES SHOW PROGRESS: the download used to sit at nothing for a hundred megabytes; there is now a real progress bar, a line saying which step is running, and an Undo the last update button. Also fixed: ready-made .forge patches are backed up by name so installing a second one can no longer destroy the first, the mod library and the updater both refuse addresses they were not meant to reach, and several messages that used to show raw error text now say what happened in a sentence.

---

| | |
|---|---|
| Package | `Workshop_v0.14_update.zip` |
| Size | 62.6 MB (65643304 bytes) |
| SHA-256 | `5ed26ab547425480d04f960d32479734d6ac84c2510f5df1c005de496f66583e` |
| Files | 485 |

The Workshop checks this SHA-256 before it installs anything; if the bytes do not
match, nothing is written.
