# 2.20-Client-Files

The non-compiled files shipped to Helbreath players: sprites, sounds, music, maps, fonts, contents and executables.

## Contents

There is no official full 2.20 client install. The closest available is built in two commits on `original`:
1. the retail **2.02** install, extracted from `Hb202full_ENG.exe` on the 2001 retail ISO;
2. the official **2.23** patch applied over it.

So 2.23 is the closest to 2.20 that exists. The client's `MAPDATA/` folder is not here: its `.amd` maps come from
[2.20-Map-Files](https://github.com/Original-Helbreath/2.20-Map-Files). Precompiled binaries (`Helbreath.exe`, `HelGame.exe`, the DLLs) are not here;
they are kept for reference in [2.20-Reference](https://github.com/Original-Helbreath/2.20-Reference). About 49 sprite paks and some sounds that the 2.20 client loads are in neither (see the project board).
The `.pak` format is documented in [PAKLib](https://github.com/shadowevil/PAKLib).

## Branches

| Branch | Purpose |
|---|---|
| `original` | The files exactly as found. Read-only by convention: never commit here. (It is not protected yet, because the org is on GitHub Free and its repos are private.) |
| `development` | Integration branch. Work happens in feature branches, which merge into `development`. |
| `stable` | Default branch. `development` is merged here once it is stable. |

## Project

Part of [Original Helbreath](https://github.com/Original-Helbreath): keeping the original 1999-2005 Siementech Helbreath alive.
Repos are named `<version>-<Part>`; other versions follow the same pattern.
Issues are tracked on the [project board](https://github.com/Original-Helbreath/projects/1). The analysis behind everything is in
[2.20-Documentation](https://github.com/Original-Helbreath/2.20-Documentation).
