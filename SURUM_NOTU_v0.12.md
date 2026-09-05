# Workshop v0.12

**Weapon stats, part swapping, and two fixes that came straight from the Discord.**

## Weapon stats (new)

Weapons tab → **WEAPON STATS**. Change a weapon's **damage**, **draw speed**,
**shot distance** and **max chain takedown**.

* Every value you can pick shows **how many other weapons share it**, so you always
  know what a change touches. Picking an existing value moves only your weapon —
  no other weapon changes.
* A value the game cannot express is **refused**, and the message lists the values
  you can actually pick.
* Nothing is written until you press APPLY **and then confirm the summary**. If the
  selection changes after the summary, the write is refused.
* **Revert stats** puts the original numbers back.

Both halves of a dual weapon move together, so a pair keeps one number.

Verified in game: Captain Drake's Swords read **17** damage instead of 38 after the
change, and **2** max chain takedown (untouched), then reverted byte-for-byte.

## Swap parts (new)

Weapons/Outfits tab → **Swap parts…**. Move a part of an item onto another of its
own slots. One click puts **the same sword model in both hands**, and the textures
follow the shape. Preview opens the same report as IMPORT 3D — nothing is written
until you confirm.

## IMPORT 3D fixes

* **Deleted faces are now reported.** If a part comes back with faces missing, the
  report says which part and how many, and tells you that removing a separate item
  (a necklace, a belt, a hat) means deleting the whole **object** in Blender's
  Outliner — deleting faces inside a part cuts a hole in the body itself.
* **A refused part now tells you the truth.** It used to say "the game archive
  changed since this export", which reads like a game update. Usually it is a
  Workshop patch already installed on that part — often from a **different outfit**,
  because some parts are shared by several items. The message now names the patch to
  revert and how many items share the part.

## Also

* Weapon Stats is translated into Spanish, Russian, Simplified Chinese and Turkish
  along with the rest of the app.
* README updated: weapon stats are no longer listed as impossible.

## Notes

Weapon stats are **balance data, not geometry**. The panel is marked BETA. Weapon
**perks** are data we can reach, but their description text lives in the localisation
package, which is not decoded yet — so a swapped perk would still show the original
wording.

Every write goes through the same safety path as the rest of the tool: backup,
journal, refusal while the game is running, and a full revert.
