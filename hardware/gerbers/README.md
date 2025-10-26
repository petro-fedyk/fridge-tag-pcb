# Gerber Files Directory

This directory contains the Gerber files required for PCB fabrication.

## File Naming Convention

The following Gerber files should be generated from the KiCad project:

| File Extension | Layer Description |
|----------------|-------------------|
| .GTL | Top Copper Layer |
| .GBL | Bottom Copper Layer |
| .GTS | Top Solder Mask |
| .GBS | Bottom Solder Mask |
| .GTO | Top Silkscreen |
| .GBO | Bottom Silkscreen |
| .GKO | Board Outline (Keep-Out) |
| .TXT or .DRL | Drill File |

## Generating Gerber Files from KiCad

1. Open the PCB file in KiCad Pcbnew
2. Go to File → Plot
3. Select the following layers:
   - F.Cu (Front Copper)
   - B.Cu (Back Copper)
   - F.SilkS (Front Silkscreen)
   - B.SilkS (Back Silkscreen)
   - F.Mask (Front Solder Mask)
   - B.Mask (Back Solder Mask)
   - Edge.Cuts (Board Outline)
4. Set Plot format to "Gerber"
5. Check "Use Protel filename extensions"
6. Click "Plot"
7. Click "Generate Drill Files"
8. Select "Excellon" format
9. Click "Generate Drill File"

## File Contents

Currently, this directory contains placeholder information. Gerber files will be generated once the PCB layout is finalized in KiCad.

## Verification

Before sending to fabrication:
1. Review all Gerber files in a Gerber viewer (e.g., gerbv, KiCad GerbView)
2. Verify board dimensions
3. Check layer alignment
4. Confirm drill holes are correctly positioned
5. Verify copper clearances meet design rules

## Notes

- Always zip all Gerber files together before sending to manufacturer
- Include a README or fab notes if any special requirements exist
- Typical file size: 500KB - 2MB (zipped)
