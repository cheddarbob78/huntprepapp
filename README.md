# huntprepapp season data

`seasons.json` holds the default NY hunting season dates used by the [NY Hunt Prep](https://github.com/cheddarbob78/huntprepapp) iOS app. The app fetches this file on launch so season dates can be corrected or updated (e.g. when NYSDEC adds a new season) without shipping a new build.

`rut.json` works the same way for the app's rut-activity estimate — a general Northeast/NY whitetail rut timeline (Pre-Rut → Seeking → Chasing → Peak Rut → Post-Rut), not tied to a specific WMU or zone.

## Editing seasons.json

- `kind` must exactly match one of the app's `SeasonKind` raw values (see `Models/Season.swift` in the app project): `Turkey – Spring`, `Deer – Early Antlerless`, `Deer – Bowhunting`, `Deer – Regular Firearms`, `Deer – Late Muzzleloader`.
- `start` / `end` are `yyyy-MM-dd` dates.
- `southern` and `northern` are the two hunting zones NY uses for deer season structure.
- Bump `updatedAt` (or `year`) whenever you change dates — the app only re-applies the file when this changes, so it won't silently overwrite a season window someone edited by hand in the app unless there's actually a new version to pull.

These are still just defaults — always cross-check against [NYSDEC's official season dates](https://dec.ny.gov/things-to-do/hunting/deer-bear/seasons) before hunting.

## Editing rut.json

- `phase` must exactly match one of the app's `RutPhase` raw values (see `Models/Rut.swift`): `Pre-Rut`, `Seeking`, `Chasing`, `Peak Rut`, `Post-Rut`.
- `start` / `end` are `yyyy-MM-dd` dates — no zone split, since rut timing barely shifts across NY's latitude range.
- `summary` is the one-line behavior note shown on the Hunt tab's rut card for that phase.
- Bump `updatedAt` whenever you change dates, same dedup behavior as `seasons.json`.

This is a rough estimate, not a location-specific prediction — actual rut timing varies with weather and local deer density.
