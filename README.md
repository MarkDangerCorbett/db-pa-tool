
# d&b PA Tech Tool

https://markdangercorbett.github.io/db-pa-tool/

A browser tool for working with d&b audiotechnik ArrayCalc v12 (`.dbpr`) project files. Built for systems engineers who need to calculate, convert, and export rigging and array data.
Everything runs client-side in a single HTML file. No data leaves the device. Will even run offline once loaded.

## What it does

Load an ArrayCalc `.dbpr` and work across these tabs:

- **Swag Calc** — catenary/cable-drop calculator. Either choose an array to work with or keep it a generic calculator. if you nload an array it will help work out needed cable lengths for your hangs. Gives warnings if cable swag is below bottom height of pa. If using compression mode it will warn if cable is near grab link. Will let you know if you need to move bridge truss if you want to bring the array in -thanks Ryan.  Advanced mode adds cable-weight and tension (truss / PA / horizontal); cable tension at the PA end flows through to rigging motor loads. I added made up threshold for tension-to-weight ratio to warn if cable might pull array too much. Assumes bridge truss heigth is same as highest array frame. Lock/unlock bridge height allows you to set bridge hieght per array. Default distance is 1.82m/6ft, default swag 7.62m/25ft. I know it would be cool to work out swag length for mains when cable goes over sub array...but i cant work out a practical way of automating that. Use the flown sub swag length, add the main swag length and add 1.2m...easy

- **Pinning** — Generates array pin sheets and acviewer files. Pin sheet has all the info a pa tech needs and very little else. Add comments, delta option. Supports tension or compression mode, with the (T)/(C) hole shown per box. Mixed-array transition handling. Also exports modified .dbev files that include load bar position, bottom height, and site angle in the source name. Also does metric and ft/in conversion on the fly.
Advanced pinning is a dangerously good idea and a work in progress. It expands on how i think pinning info should be displayed. use with caution.
- **FF Spacing** — point-source group spacing. Two modes, spacing and coverage. Spacing: load data from file. brings cabinets and spaces them to the stage size. simple. Coverage: this is the real heavyweight here. pulls series and cabinet data from file. allows you to adjust rotation/model within series (click on a cabinet), add a thrust etc. Each provides .dbep for feeding back into arraycalc.
- **Sub Spacing** — simple and thrust mode. Simple is as it sounds. Get data from file, adjust spacing. Ff you click on the cabinet it will rotate and adjust spacing. shows c-c spacing and edge-edge. Thrust mode is same but allows you to define or import thrust data. works out the spacing given the thrust dead zone. Both modes can output .dbesa files for importing back into arraycalc. CHECK CABINET NUMBERS! only exports positional data back to arraycalc!
- **CAD Stuff** — DXF export (R12/AC1009) of rigging points: Import from file, gets array info and cable swag weight info. sets motor type threshold. If total array weight is over 450 kg it removes ability to use 1/2ton, if over 950kg prevents use of 1ton. user can opt to use higher capacity tho. Input where /if you want delta plate. adjust allowable motors. adjust delta point spread. adjust fleet if you want. The fleet number defaults to the spacing between load points on array. Export dxf creates dxf file with motor symbols as CAD blocks, delta geometry, fleet distance, laser and dispersion lines. making adjustments feeds data to point conversion.
- **Point Conversion** — convert coordinates between `.dbpr`, CSV, and `.dbacv` venue-point exports. Can pull modified rigging points straight from CAD Stuff. If you pull from csv file it asks which column is which. can name points in table. .csv will export a csv file. dbev file exports points as rigging point elements to import back to array calc.
- **Other Calcs** — right-angle triangle, angle translator, wavelength/delay. pretty basic really.


## Status

Beta. Verify every figure against d&b documentation before rigging anything. This tool is a calculator, not a substitute for ArrayCalc or a qualified rigger.

## Disclaimer

Not affiliated with, authorised by, or endorsed by d&b audiotechnik GmbH & Co. KG. "d&b audiotechnik", "ArrayCalc", and product names are their trademarks. Cabinet data is from publicly available datasheets, for reference only.

## Licence

Proprietary. Copyright &copy; 2025 Mark Danger. All rights reserved. No permission to copy, modify, redistribute, or reverse-engineer without written permission. Bundled sql.js retains its own MIT licence.
