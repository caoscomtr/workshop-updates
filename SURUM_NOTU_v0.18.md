# Workshop v0.18

_2026-10-26_

PATCHED OUTFITS FIXED: the September game patch replaced the meshes of 16 outfits (Altair, Connor, Ezio, Templar, Whaler, Stealth and others) and added new pieces. Workshop read and wrote the old copies, so exports showed old meshes and edits such as Hide parts or Import 3D never showed in game. It now reads and writes the copy the game actually uses, and the new pieces (Altair's skirt and belt flaps) appear in the parts list. On the few outfits whose material was patched, painting writes the full-size textures and tells you the small far-distance levels stay original. STUCK AFTER AN INTERRUPTED PAINT JOB: if a paint job was cut off and the game updated later, Workshop refused to revert or paint again. Health Check now shows one clear line and a Clear stuck job button; it moves the old record to a dated folder and deletes nothing. STARTUP: on slow starts the window could show "api.baslangic is not a function" or come up empty; it now waits until the app is really ready. GAME FOLDER: choosing the game folder no longer depends on the Windows folder window, which hangs on some PCs; the new Game folder panel lists the installs found on your PC and lets you paste a path. SOUNDS: searching for what you hear now works - assassination, hidden blade, kill, pistol, cannon and similar words find the right sound banks. HEALTH CHECK: lists leftover DLL/ASI mod files in the game folder (a common cause of crashes when loading a save) and actually tests the texture encoder; if Windows Smart App Control blocks it, Health Check and the paint tools say so plainly instead of failing with a technical error. NAMED FIELDS: the XML view now names 114 fields in 30 classes (was 58 in 17): entity placement (position and rotation), level-of-detail distances, bounding boxes, ship upgrade prices, cannon and mortar damage, ammunition and crew capacities, colours. Fields marked measured or guess say how sure we are.

---

| | |
|---|---|
| Package | `Workshop_v0.18_update.zip` |
| Size | 63.7 MB (66806315 bytes) |
| SHA-256 | `6e51f8c5def18f02f99813bfdb9a7abd7ac9e59751031f4144dd9db876b6ae97` |
| Files | 502 |

The Workshop checks this SHA-256 before it installs anything; if the bytes do not
match, nothing is written.
