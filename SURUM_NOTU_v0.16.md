# Workshop v0.16

_2026-09-09_

EXPLORER TREE: the Explorer now lists an archive as a tree - archive, type, class, entry and the files inside each entry - with a Type column, type chips and instant search over every row; click an inner file to open it as XML. LENGTH-CHANGING RAW EDITS: a .bin you exported from the Explorer or with Unpack all can be put back even when its size changed; Workshop rewrites the inner file's own size field, appends the new bytes and redirects the table of contents, so the original is never overwritten and Revert restores it. A file whose wrapper header is damaged is refused before anything is written. Also fixed: the README header still showed an old version; Restore All left hidden parts, ship stats, XML edits and imported meshes in place - it now reverts every record Workshop wrote and says what it could not.

---

| | |
|---|---|
| Package | `Workshop_v0.16_update.zip` |
| Size | 63.5 MB (66534231 bytes) |
| SHA-256 | `2c7c1e775d86bf6c3231511af8ea5f8cec2de753ea6f5f637171c5b2e2437929` |
| Files | 497 |

The Workshop checks this SHA-256 before it installs anything; if the bytes do not
match, nothing is written.
