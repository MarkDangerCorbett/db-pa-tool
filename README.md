
# d&b PA Tech Tool

https://markdangercorbett.github.io/db-pa-tool/

A self-contained, offline browser tool for working with d&b audiotechnik ArrayCalc v12 (`.dbpr`) project files. Built for systems engineers who need to calculate, convert, and export rigging and array data.
Everything runs client-side in a single HTML file. No data leaves the device. 

## What it does

Load an ArrayCalc `.dbpr` and work across these tabs:

- **Swag Calc** — catenary/cable-drop calculator. Advanced mode adds cable-weight and tension (truss / PA / horizontal); cable tension at the PA end flows through to rigging motor loads.
- **Pinning** — line-array pin sheets in tension or compression mode, with the (T)/(C) hole shown per box. Mixed-array transition handling. PDF export for the riggers.
- **FF Spacing** — point-source group spacing, `.dbep` export back into ArrayCalc.
- **Sub Spacing** — simple and thrust sub arrays, per-position rotation, `.dbesa` export. Cabinet dimensions sourced from d&b datasheets.
- **CAD Stuff** — DXF export (R12/AC1009) of rigging pick points: motor symbols as CAD blocks, delta bridle geometry, fleet override, laser and dispersion lines.
- **Point Conversion** — convert coordinates between `.dbpr`, CSV, and `.dbacv` venue-point exports. Can pull modified rigging points straight from CAD Stuff.
- **Other Calcs** — right-angle triangle, angle translator, wavelength/delay.


## Status

Beta. Verify every figure against d&b documentation before rigging anything. This tool is a calculator, not a substitute for ArrayCalc or a qualified rigger.

## Disclaimer

Not affiliated with, authorised by, or endorsed by d&b audiotechnik GmbH & Co. KG. "d&b audiotechnik", "ArrayCalc", and product names are their trademarks. Cabinet data is from publicly available datasheets, for reference only.

## Licence

Proprietary. Copyright &copy; 2025 Mark Danger. All rights reserved. No permission to copy, modify, redistribute, or reverse-engineer without written permission. Bundled sql.js retains its own MIT licence.
