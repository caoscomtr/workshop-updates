# Workshop v0.13

**A bug-fix release. One of these was serious enough that weapon mods only half worked.**

## Weapons were only half-patched

A weapon is not one mesh. Captain Drake's Swords, for example, is **eight** mesh
entries: two groups, four distance bands each. IMPORT 3D was writing only the
closest band — and on 97 of the weapon groups the game actually draws the **second**
band beyond one metre.

So your edit showed up in the inventory, and the original came back the moment the
camera pulled away in a fight. Across the whole weapon catalogue **249 of 364 mesh
entries were never being written**, and the tool still reported SUCCESS.

It now writes your shape to every band the game draws up close and at mid range.
Verified in game. The far proxy meshes keep the original outline — writing a fully
detailed model into a 32-metre proxy would cost about nine times the polygons for
something you cannot see — and the report tells you which bands were covered.

## Revert now really restores

From the second import onward, "Revert all" was leaving the archive permanently
larger while claiming it had been restored. It now trims the archive back to its
original size and reports how many bytes came off. If it cannot trim (because
another patch was written after this one) it says so, and says what to do about it,
instead of claiming success.

## A patched entry is no longer locked after a game update

Once a mesh had been patched, a game update — or Steam's "verify file integrity" —
made that entry permanently un-installable: the plan looked fine and the write was
refused as "backup damaged". The stale record is now recognised as stale, cleared,
and you can install again. A genuine conflict with another tool is still refused.

## Smaller, but they cost people time

* **Shared parts now warn you when you write.** Some parts are drawn by many items —
  the body mesh is shared by 24 outfits. Editing one changed all of them silently.
  The report now says "shared by N other items" before you write, not only when hiding.
* **A half-written import is rolled back.** If one band of a weapon fails, the bands
  that already went in are removed instead of leaving the item in a mixed state and
  reporting success.
* **When parts are missing from your file**, the report no longer just says "nothing
  will be written". It names them and offers to hide them, and the checkbox is
  highlighted. Four people hit that wall.
* Deleting files in the game folder never undid anything — Workshop writes into
  `DataPC_boot.forge`, not the patch file. The README says so now.

## Notes

Writing an extra band costs space: a band entry grows to roughly twice its size, so
one weapon import can add up to ~600 KB to the archive. Revert takes all of it back.

Cross-import (Swap parts) still has not been checked in game.
