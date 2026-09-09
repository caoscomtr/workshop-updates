# Workshop v0.17

_2026-09-09_

RAW ENTRIES: the Explorer tree now lists the archive's raw entries too - external mip levels and streamed mesh pages that are not containers - under the raw type; they show their id, export as bytes and cannot be opened as XML. DUPLICATE AS NEW ENTRY: pick a container entry, give it a new name, and Workshop appends a copy as a brand-new row in the archive's table of contents with its own id; Revert removes it again. The game will not use the new entry until a data record points at it, so this is the first half of adding content, not the whole of it. DDS TEXTURES: export any texture as a .dds with every mip level exactly as the game stores it, and import a .dds back without re-encoding when its format, size and mip count match; Add a Mod now accepts community .dds files. While proving this, a writer bug came out: textures that are not square were laid out wrongly in the mip pool, so an import could report success and change nothing - fixed and measured. EXPERT MODE: in Edit as XML, tick Expert mode and an edit that changes the byte length of an object is written instead of refused - Workshop rebuilds the container's own size field, re-serialises the block and redirects the table of contents, then lists what it could not check: counts inside the object that point at the changed part are yours to keep right, and Revert restores the original. The switch is off by default and the confirmation drops whenever it is flipped. NAMED FIELDS: the XML view now names the fields Workshop itself understands - ship stats, weapon stats, texture descriptors, texture set slots, mesh headers, sound ids - with the source of each name and a comment showing the value and unit; the names come from our own engines, not from any other tool, and the rest of the fields stay positional until we learn them. CLASS NAMES FROM THE GAME: the game ships its own class dictionary inside its data; Workshop now reads it, so nearly every entry in the Explorer tree and the XML view shows its real class name instead of a hash, and twelve names in the old table that were hash collisions are corrected. No third-party dictionary is used.

---

| | |
|---|---|
| Package | `Workshop_v0.17_update.zip` |
| Size | 63.7 MB (66757226 bytes) |
| SHA-256 | `540873e0a3c57dd95fa18cdf2362ac2efaf52e8540b81b2516dd533837b36fea` |
| Files | 501 |

The Workshop checks this SHA-256 before it installs anything; if the bytes do not
match, nothing is written.
