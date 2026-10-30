# Tricky Madness mod catalog

The list of mods and map packs the Tricky Madness mod manager can install.

- `catalog.json` — one entry per mod or pack. The zips themselves stay on MEGA;
  each build names a shared MEGA folder (`sources`), a subfolder (`path`) and a
  file name, plus the zip's size and sha256 and every file it installs with its
  own hash.
- `thumbs/` — 640×360 menu art.
- `catalog.schema.json` — the format. A copy; the authority is
  `release_shared/catalog.schema.json` in the mods repo.

## Updating

Don't hand-edit sizes, hashes or `files`. They come from the zip:

    release_shared/catalog_entry.py add "<zip>"     # mega_release.sh runs this after an upload
    release_shared/catalog_entry.py links           # copy MEGA folder share links in
    release_shared/catalog_entry.py check           # validate

Hand-edit only `name`, `description`, `thumb`, `video`, `author` and `kind`;
`add` keeps them. Map packs get `requires.level-hook` from the "Hook this pack
was built and tested against" line in their README.

A source whose `link` is `null` has not been shared yet, so its entries show in
the list but cannot be installed.
