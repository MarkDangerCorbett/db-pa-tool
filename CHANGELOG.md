# d&b PA Tech Tool — Changelog

Versioning: `major.minor.patch` (e.g. 0.98.01). Patch = small point updates.

---

## 0.98.02
- **Fixed `.dbep` (FF Spacing) export crashing ArrayCalc.** Export renumbers box `UniqueId` to 1000+ but was copying the original `Linked` values, which point at the source project's old UniqueIds — dangling references → crash. Now forces `Linked="0"` (matches the SubArray export). Verified against a known-good `.dbep` from the same project. (`Symmetric` left as-is — a known-good file uses `Symmetric="1"` with both sides explicit, so it was never the problem.)

## 0.98.01
- Changelog started. Adopted three-part version numbers for small point updates.

## 0.98
- **Fixed imperial `.dbev` export.** ArrayCalc stores all coords/weights/forces in SI (metres, kg, kN); `UnitLength`/`UnitWeight` are display flags only. Export was multiplying stored values by 3.28084 **and** flipping the flag — double conversion, geometry 3.28× oversized. Now keeps SI values, flips flags only. Metric and imperial files are identical except the two flags + ft/in labels in source-group names.

## 0.97
- Banner sign-off spacing tweak.

## 0.96
- Reverted contact email.

## 0.94–0.95
- Contact email churn (later reverted). Added "job offers?" to banner.

## 0.93
- Banner email is now a mailto link.

## 0.92
- Added contact line to top banner: "bugs? feature requests? abuse? …".

## 0.91
- **Default to dark mode** (unless user has explicitly chosen light — persists via localStorage).
- Added orange top banner: "STILL IN BETA! Double check all numbers!".

## 0.9
- Reworded horizontal-tension warning: "…exceeds my made up 5% threshold. Might cause PA to become wonky."

## 0.89
- Legal page footer header now orange to match section style.

## 0.88
- "Legal stuff" is a button. Added footer to legal page.

## 0.87
- Added file header comment (copyright + sql.js MIT notice).
- Added **Legal Stuff** page (licence, third-party sql.js MIT, d&b trademark disclaimer, offline/privacy) with link from Read Me.

## 0.86
- Rewrote Advanced Pinning Read Me blurb (compression mode, dash-shift behaviour, mixed T/C transition box).

## 0.85
- Read Me: dropped `.dxf` mention from Import blurb; added Swag Advanced paragraph (tensions, cable-weight flow-through, motor step-up); expanded Pinning section.

## 0.84
- Right-angle triangle calc: diagram stays full colour when reset (visual guide); "Long" label runs vertical along the long edge.

## 0.83
- Version-bump only ship.

## 0.82
- Laser + dispersion lines now originate from the original front pick (red cross), not the fleet-adjusted point.
- Renamed pick-point layer to `FRAME_PICKUPS` (R12/AC1009 rejects spaces in layer names).

## 0.81
- **CAD Stuff table:** added read-only **Pick Dist (m)** column (front↔rear pick separation from `.dbpr`); **Fleet** defaults to that distance, editable. Fixed 7-header/6-cell misalignment.
- **Sub Spacing simple mode:** rotate toggle now survives adding/removing subs — `subPositionsM` rebuilt on every count change, rotations preserved by nearest-Y; SVG reads rotation by Y-match not stale index.
- **Sub dimensions:** J-SUB kept `[1100, 540]` (wide, stacks on J8/J12). 21S-SUB fixed to `[580, 1100]`. B22-SUB `[1160, 585]` confirmed from datasheet. Q-SUB/B2-SUB/V-SUB/XSL-SUB/SL-SUB datasheet-verified. V-SUB, V-GSUB, Q-SUB, Q-GSUB added to NO_ROTATE (fixed-orientation cabinets — always use width).

## 0.8
- **Deep review + regression fixes.** The v0.731 restore-from-base had silently reverted several features; all restored:
  - Fleet override (reads `rigFleet_`, recentres on midpoint, extends fleet/2 each side).
  - Original pick crosses drawn at file coords, independent of fleet.
  - Thrust rotation export fix (0.005 tolerance, arrays hoisted out of map, bounds-checked) — stops wide thrust subs self-rotating in export.
  - Delta spread field greys out when delta = none.
- Fixed cable-weight double-count in the live-patch (subtract stale cable before adding T_P).
- Fixed `.dbacv` name doubling ("Main L Front Front").
- Stripped dead `_TRUSS_DATA` (9.3 KB) + `exportF44TrussDXF`.
- Verified against real project (War on Drugs / Royal Blood): fleet geometry, motor ratings (Main 910 kg → 1t, Sides 396 kg → ½t), DXF valid AC1009.

---

## 0.689 → 0.757 (summary — earlier sessions)
Detailed per-version history for this range is in the dev transcripts. Key work:
- **Point Conversion tab** (renamed from Rigging Plot): `.dbpr`/CSV → `.dbacv` venue-point export, inline CSV column-role picker, name dedup, per-row motor dropdown.
- **CAD Stuff tab** split out: rigging DXF export (R12/AC1009) with motor symbols as CAD blocks, delta bridle geometry, fleet/laser/dispersion lines.
- **Cable weight flow-through:** Swag Calc advanced → tension at PA end adds to array weight → flows to Point Conversion + CAD Stuff rear motor loads, steps up motor rating over threshold.
- **Motor minimum rating** (safety-critical): thresholds <450 kg = ½t, 450–949 = 1t, ≥950 = 2t, consistent across all code paths.
- **Import page** reports arrays, point sources, subs, stage planes, catwalks.
- **Truss DXF export** attempted then abandoned (AutoCAD crashed on 3D geometry).
- Recurring bug classes fixed: JS template-literal `</script>` breaking the HTML parser; var-before-use ordering; R12 layer names with spaces.

*Versions before 0.689 predate the retained transcripts — no clean per-version record.*
