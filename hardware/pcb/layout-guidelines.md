# PCB Layout Guidelines

## Layer Stack-Up

```
Layer 1 (Top):    Signal + Components
Core:             FR-4 (1.6mm)
Layer 2 (Bottom): Ground Plane + Battery Holder
```

## Component Placement Strategy

### Top Side
```
┌─────────────────────────────────────────────┐
│  [SW1]                            [LED1+R3] │
│                                              │
│         ┌──────────────┐                    │
│         │   ESP32-32   │          [C1][C2]  │
│         │   WROOM      │          [R1][R2]  │
│         └──────────────┘                    │
│                                              │
│                    ┌──────┐                 │
│                    │DHT22 │                 │
│                    └──────┘                 │
│  (M2.5)                            (M2.5)   │
└─────────────────────────────────────────────┘
```

### Bottom Side
```
┌─────────────────────────────────────────────┐
│                                              │
│           ┌──────────────┐                  │
│           │  CR2032      │                  │
│           │  Battery     │     [USB-C]      │
│           │  Holder      │     [U3]         │
│           └──────────────┘                  │
│                                              │
│  (M2.5)                            (M2.5)   │
└─────────────────────────────────────────────┘
```

## Routing Guidelines

### Power Distribution

1. **VCC Traces**:
   - Minimum width: 0.5mm
   - Route on top layer
   - Star topology from battery to each component
   - Place decoupling caps as close as possible to IC pins

2. **Ground Plane**:
   - Solid copper pour on bottom layer
   - Multiple vias connecting top ground to bottom plane
   - Via placement near each component ground pin

### Signal Routing

1. **DHT22 Data Line**:
   - Keep trace short (<50mm)
   - Route away from power switching circuits
   - Add 10kΩ pull-up resistor close to ESP32

2. **GPIO Signals**:
   - Minimize trace length
   - Avoid running under or near ESP32 antenna
   - Use 0.2mm minimum trace width

3. **USB Data Lines** (if used):
   - Differential pair routing (D+ and D-)
   - Match lengths (within 5mm)
   - 90Ω differential impedance
   - Keep away from noisy signals

### RF Considerations

1. **ESP32 Antenna Area**:
   ```
   ┌────────────────┐
   │                │  ← 5mm keepout zone
   │   ESP32        │
   │   [Antenna]    │  ← No copper, components, or vias
   │                │
   └────────────────┘
   ```

2. **Ground Plane Under ESP32**:
   - Solid ground except under antenna
   - Multiple vias around perimeter
   - Connect thermal pad to ground with vias

### Thermal Management

1. **Component Spacing**:
   - Minimum 2mm between large components
   - DHT22 sensor isolated from heat sources
   - Good airflow path to sensor

2. **Copper Pour**:
   - Full ground plane aids heat dissipation
   - Thermal relief on ground connections for hand soldering

## Design Rules (DRC Settings)

### Clearances
- Track to Track: 0.2mm
- Track to Pad: 0.2mm
- Pad to Pad: 0.2mm
- Track to Via: 0.2mm
- Via to Via: 0.4mm
- Track to Edge: 0.3mm

### Track Widths
- Signal: 0.2mm minimum
- Power (VCC): 0.5mm minimum
- Ground: 0.3mm minimum

### Via Specifications
- Finished Hole: 0.3mm
- Pad Diameter: 0.6mm
- Annular Ring: 0.15mm minimum

### Solder Mask
- Expansion: 0.1mm from pads
- Minimum web: 0.15mm

### Silkscreen
- Line Width: 0.15mm
- Text Height: 1.0mm minimum
- Clearance from pads: 0.15mm

## Critical Dimensions

### Board Outline
- Size: 50.0mm x 30.0mm (±0.2mm)
- Corner radius: 2mm (optional)
- Edge clearance: 0.5mm from components

### Mounting Holes
- Diameter: 2.7mm (for M2.5 screws)
- Position: 3mm from corners
- Clearance: 5mm radius (no copper)

## Fabrication Notes

### Test Points
Add test points for:
- VCC
- GND  
- GPIO4 (DHT22 data)
- GPIO0 (Boot mode)
- EN (Reset)

### Fiducial Marks
- Place 3 fiducials for SMT assembly
- 1mm diameter circular pads
- Bare copper (no solder mask)
- Positioned at board corners

### Panelization
- For production: 5x5 array on 250x250mm panel
- V-groove or tab-route separation
- 5mm spacing between boards

## Manufacturing Tolerances

| Feature | Tolerance |
|---------|-----------|
| Board dimensions | ±0.2mm |
| Hole position | ±0.1mm |
| Track width | ±0.05mm |
| Layer alignment | ±0.1mm |
| Solder mask registration | ±0.1mm |

## Quality Checks

### Pre-Manufacturing
- [ ] DRC clean (zero errors)
- [ ] All footprints verified
- [ ] Silkscreen readable
- [ ] No text on pads
- [ ] Mounting holes correctly sized
- [ ] Polarity markings clear

### Post-Manufacturing
- [ ] Visual inspection
- [ ] Electrical testing (continuity)
- [ ] Dimensional check
- [ ] Impedance testing (if critical)

## Version Control

Track layout changes:
- v1.0: Initial layout
- Document major changes in git commits
- Tag stable releases
