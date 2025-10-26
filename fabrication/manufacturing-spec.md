# Manufacturing Specifications - Fridge Tag PCB

## PCB Fabrication Specifications

### Board Parameters

| Parameter | Specification |
|-----------|--------------|
| Board Material | FR-4 |
| Board Thickness | 1.6mm (±10%) |
| Copper Weight | 1 oz (35μm) |
| Number of Layers | 2 (Top + Bottom) |
| Solder Mask | Green (LPI) |
| Silkscreen | White |
| Surface Finish | ENIG (1-2μm Ni, 0.05μm Au) |
| Min Track Width | 0.2mm (8 mil) |
| Min Track Spacing | 0.2mm (8 mil) |
| Min Hole Size | 0.3mm (12 mil) |
| Board Outline Tolerance | ±0.2mm |

### Board Dimensions

- **Length**: 50mm ±0.2mm
- **Width**: 30mm ±0.2mm
- **Thickness**: 1.6mm ±0.16mm

### Design Rules

| Rule | Value |
|------|-------|
| Minimum Trace Width | 0.2mm (0.5mm for power) |
| Minimum Trace Spacing | 0.2mm |
| Minimum Via Diameter | 0.6mm |
| Minimum Via Drill | 0.3mm |
| Minimum Annular Ring | 0.15mm |
| Solder Mask Expansion | 0.1mm |

## Assembly Specifications

### Component Placement

1. **Top Side Components**:
   - ESP32-WROOM-32 (U1)
   - DHT22 Sensor (U2)
   - All SMD resistors and capacitors
   - Status LED (LED1)
   - Power switch (SW1)

2. **Bottom Side Components**:
   - Battery holder (BT1)
   - Optional: USB connector (J1)
   - Optional: Voltage regulator (U3)

### Solder Paste

- **Type**: SAC305 (Sn96.5/Ag3.0/Cu0.5) Lead-free
- **Stencil Thickness**: 0.12mm (0.15mm for power components)
- **Aperture Reduction**: 10% for fine-pitch components

### Reflow Profile

| Phase | Temperature | Duration |
|-------|-------------|----------|
| Preheat | 150-180°C | 60-90s |
| Soak | 180-200°C | 60-120s |
| Reflow | 240-250°C | 20-40s |
| Cooling | <6°C/s | Natural |

**Peak Temperature**: 245-250°C
**Time Above 217°C**: 60-90 seconds

## Testing Specifications

### Electrical Testing

1. **Continuity Test**:
   - All power nets
   - All ground connections
   - Critical signal paths

2. **Isolation Test**:
   - Between power and ground: >10MΩ
   - Between adjacent traces: >10MΩ

3. **Functionality Test**:
   - Power-on test (LED indicator)
   - Sensor communication check
   - WiFi/BLE connectivity test
   - Battery voltage measurement

### Visual Inspection

- Check for component placement accuracy
- Verify solder joint quality
- Inspect for bridges or shorts
- Confirm silkscreen alignment

## Quality Standards

- **IPC Class**: IPC-A-610 Class 2 (Consumer Electronics)
- **Workmanship**: IPC-A-610 Rev. G or later
- **Acceptance Criteria**: Zero defects for critical components

## Packaging

- **ESD Protection**: ESD-safe bags required
- **Quantity per Bag**: 10 boards
- **Outer Packaging**: Cardboard box with foam padding
- **Labeling**: Include version number and date code

## Special Notes

1. **Battery Holder**: Ensure polarity marking is clear
2. **ESP32 Module**: Handle with ESD precautions
3. **DHT22 Sensor**: Avoid exposure to solvents
4. **RF Antenna**: Keep clear of copper pour and components
5. **Mounting Holes**: M2.5 compatible (2.7mm diameter)

## Delivery Format

### Gerber Files (RS-274X format)

- Top Copper (GTL)
- Bottom Copper (GBL)
- Top Solder Mask (GTS)
- Bottom Solder Mask (GBS)
- Top Silkscreen (GTO)
- Bottom Silkscreen (GBO)
- Board Outline (GKO)
- Drill File (TXT/DRL)

### Additional Files

- Pick and Place (CSV)
- Bill of Materials (CSV/XLS)
- Assembly Drawing (PDF)
- Fabrication Drawing (PDF)
- IPC-2581 or ODB++ (optional)

## Lead Time

- **PCB Fabrication**: 5-7 working days
- **Assembly**: 3-5 working days
- **Testing**: 1-2 working days
- **Total**: 10-15 working days

## Minimum Order Quantity

- **Prototype**: 5 boards
- **Production**: 100 boards

## Compliance

- **RoHS**: Compliant
- **REACH**: Compliant
- **Halogen-Free**: Optional
- **UL Marking**: Not required for prototype
