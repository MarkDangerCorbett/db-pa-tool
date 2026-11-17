# d&b PA Tech Tool

A self-contained, offline browser tool for working with d&b audiotechnik ArrayCalc v12 (`.dbpr`) project files. Built for live-sound and systems engineers who need to calculate, convert, and export rigging and array data without internet access, accounts, or a backend.

Everything runs client-side in a single HTML file. No data leaves the device.

## What it does

Load an ArrayCalc `.dbpr` and work across these tabs:

- **Swag Calc** — catenary/cable-drop calculator. Advanced mode adds cable-weight and tension (truss / PA / horizontal); cable tension at the PA end flows through to rigging motor loads.
- **Pinning** — line-array pin sheets in tension or compression mode, with the (T)/(C) hole shown per box. Mixed-array transition handling. PDF export for the riggers.
- **FF Spacing** — point-source group spacing, `.dbep` export back into ArrayCalc.
- **Sub Spacing** — simple and thrust sub arrays, per-position rotation, `.dbesa` export. Cabinet dimensions sourced from d&b datasheets.
- **CAD Stuff** — DXF export (R12/AC1009) of rigging pick points: motor symbols as CAD blocks, delta bridle geometry, fleet override, laser and dispersion lines.
- **Point Conversion** — convert coordinates between `.dbpr`, CSV, and `.dbacv` venue-point exports. Can pull modified rigging points straight from CAD Stuff.
- **Amp IDs** — assign amplifier IDs (subnet.device) per EDS standard. Auto-assign with subsystem selector. Channel naming compatible with both d&b R1 (15-char limit enforced) and AutoR1. Exports assignments back into `.dbpr`.
- **Rack Build** *(beta)* — visual rack layout for amp channel assignment. Drag cabinets into channel slots, auto-assign, export to `.dbpr`.
- **Other Calcs** — right-angle triangle, angle translator, wavelength/delay.

## Hosting

It's one HTML file. Two ways to run it:

1. **Local** — open the `.html` in any modern browser. Done.
2. **GitHub Pages** — the release folder includes an `index.html` copy. Drop the folder into a repo, enable Pages, and it serves directly.

No build step, no dependencies to install.

## Tech

- Single-file HTML/CSS/JS, no framework.
- Bundles [sql.js](https://github.com/sql-js/sql.js) (MIT) to read the SQLite-backed `.dbpr`/`.dbev` files in-browser.
- DXF export is hand-written R12/AC1009 (validated against AutoCAD and `ezdxf`).

## Status

Beta. Verify every figure against d&b documentation before rigging anything. This tool is a calculator, not a substitute for ArrayCalc or a qualified rigger.

## Disclaimer

Not affiliated with, authorised by, or endorsed by d&b audiotechnik GmbH & Co. KG. "d&b audiotechnik", "ArrayCalc", and product names are their trademarks. Cabinet data is from publicly available datasheets, for reference only.

## Licence

Proprietary. Copyright &copy; 2025 Mark Danger. All rights reserved. No permission to copy, modify, redistribute, or reverse-engineer without written permission. Bundled sql.js retains its own MIT licence.
