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

## Sprites

Each sprite pak has its own folder: `SPRITES/<name>.pak/<name>.pak` is the pak, and `SPRITES/<name>.pak/extracted/`
holds one PNG and one JSON per sheet (frame rectangles and pivots, plus the bytes the client skips), made with
`pak/pak_tool.py` from [Tools](https://github.com/Original-Helbreath/Tools). `WHelm2.pak`, `WHelm3.pak` and
`WHelm5.pak` are empty files, as shipped, and have nothing extracted.

The client opens `sprites\<name>.pak` as a file, so this folder is not playable as it is. Lay out an install with
`deploy/deploy_client.py` from Tools, which copies everything and puts each pak flat in `SPRITES/`
(`--build-paks` rebuilds each pak from `extracted/` first, so edited PNGs or frames take effect).

## Data files as JSON

The client reads its text data files as JSON now (formats: 2.20-Client-Source `docs/data-formats.md`).
On this branch the following files were converted with `client-data/convert_client_data.py` from
[Tools](https://github.com/Original-Helbreath/Tools), and the original text files were removed; the
`original` branch keeps them unchanged.

| Original | JSON |
|---|---|
| `LOGIN.CFG` | `LOGIN.json` |
| `CONTENTS/contents<N>.txt`, `CONTENTS/Contents<N>.txt` (49 files) | `CONTENTS/contents<N>.json` (same names, `.json`) |
| `CONTENTS/GameMsgList.txt` | `CONTENTS/GameMsgList.json` |
| `CONTENTS/BItemcfg.txt` | `CONTENTS/BItemcfg.json` |
| `CONTENTS/MAGICCFG.TXT` | `CONTENTS/MAGICCFG.json` |
| `CONTENTS/SKILLCFG.TXT` | `CONTENTS/SKILLCFG.json` |
| `CONTENTS/badword.txt` (XOR-obfuscated) | `CONTENTS/badword.json` (plain) |

`CONTENTS/ItemName.cfg` stays a text file: the client still reads it as text. Korean strings were
cp949 in the originals; each JSON file records its source encoding. The shipped `badword.txt` uses
the older headerless XOR form, which the 2.20 client's own decoder rejected; its JSON form loads.

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
