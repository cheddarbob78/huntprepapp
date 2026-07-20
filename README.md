# huntprepapp season data

`seasons.json` holds the default NY hunting season dates used by the [NY Hunt Prep](https://github.com/cheddarbob78/huntprepapp) iOS app. The app fetches this file on launch so season dates can be corrected or updated (e.g. when NYSDEC adds a new season) without shipping a new build.

## Editing

- `kind` must exactly match one of the app's `SeasonKind` raw values (see `Models/Season.swift` in the app project): `Turkey – Spring`, `Deer – Early Antlerless`, `Deer – Bowhunting`, `Deer – Regular Firearms`, `Deer – Late Muzzleloader`.
- `start` / `end` are `yyyy-MM-dd` dates.
- `southern` and `northern` are the two hunting zones NY uses for deer season structure.
- Bump `updatedAt` (or `year`) whenever you change dates — the app only re-applies the file when this changes, so it won't silently overwrite a season window someone edited by hand in the app unless there's actually a new version to pull.

These are still just defaults — always cross-check against [NYSDEC's official season dates](https://dec.ny.gov/things-to-do/hunting/deer-bear/seasons) before hunting.
