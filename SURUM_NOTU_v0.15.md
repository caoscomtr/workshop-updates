# Workshop v0.15

_2026-09-08_

SHIP STATS: you can now change the Jackdaw's hull health, ram damage and speed from the Ships tab. Pick a value, press Apply to see exactly which bytes change, then Write to the game; Revert puts the original numbers back. The write was proven in the real game - the archive loaded to the main menu with the change in place and came back byte-for-byte after Revert. Hull health levels 1 to 5 are the game's own upgrade ladder (600 to 5000), so a new game starts at whatever you set level 1 to. HIDE PARTS: on any outfit, character or weapon, tick the parts you do not want - a hood, a coat, a holster, a long skirt - and they are hidden in the game without Blender; every distance level of the part is hidden, not just the closest one, and Show again restores them. This also fixes Swap parts, which used to write only the closest distance level of an outfit part, so the change showed in the preview but the original came back the moment the camera pulled away. EDIT AS XML: the Explorer can open any entry as a readable XML dump, let you change a value or a reference, show which bytes will change, and write it back; edits that would change the length of an object are refused with a message that says so. UNPACK ALL: extract every entry of an archive to a folder, edit what you want, then Find changed files and Put them back - only the files you touched are written. MERGE PATCHES: drop two ready-made .forge patches at once, or a second one while another is installed, and the Workshop combines them into one patch instead of overwriting; where both change the same part of the game it tells you which one wins. Also fixed: a texture you had reverted could still show as PATCHED on the Ships tab - stale records from an older archive identity were counted as live; they are now closed on revert and ignored when reading. Rolling back an update twice used to restore the same backup twice and leave you on the version you thought you had left; each backup is now used once, and when none is left the Workshop says so instead of pretending.

---

| | |
|---|---|
| Package | `Workshop_v0.15_update.zip` |
| Size | 63.4 MB (66515952 bytes) |
| SHA-256 | `deac6ed0fbe57af538e614cb9f38381a3d15b902dbb77074917e4da7cd9da8eb` |
| Files | 497 |

The Workshop checks this SHA-256 before it installs anything; if the bytes do not
match, nothing is written.
