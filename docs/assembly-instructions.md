# Assembly Instructions - Fridge Tag PCB

## Required Tools

- Soldering iron (temperature controlled, 300-350°C)
- Solder wire (SAC305 lead-free or 63/37 leaded)
- Tweezers (fine tip)
- Flux pen or flux paste
- Multimeter
- Magnifying glass or microscope (optional but helpful)
- Isopropyl alcohol (IPA) for cleaning
- ESD mat and wrist strap

## Component Assembly Order

Follow this order for hand assembly to minimize rework:

### Step 1: Prepare the PCB
1. Clean the PCB with IPA to remove any contaminants
2. Apply flux to all SMD pads
3. Use proper ESD precautions throughout assembly

### Step 2: SMD Components (Smallest First)
1. **Resistors (R1, R2, R3)** - 0805 package
   - Apply small amount of solder to one pad
   - Place component with tweezers
   - Solder first pad, then second pad
   - Touch up first pad if needed

2. **Capacitors (C1, C2)** - 0805 package
   - Same technique as resistors
   - Pay attention to polarity for tantalum caps (if used)

3. **LED (LED1)** - 0805 package
   - Note polarity: cathode mark on component
   - Align with silkscreen polarity indicator

### Step 3: Integrated Circuits

4. **Optional: AMS1117 Regulator (U3)** - SOT-223
   - Apply flux to all pads
   - Align pin 1 with PCB marking
   - Solder one pin to tack in place
   - Solder remaining pins
   - Use solder wick to remove any bridges

5. **ESP32-WROOM-32 (U1)**
   - **IMPORTANT**: This is the most critical component
   - Apply flux liberally to all pads
   - Carefully align module with pads (use silkscreen outline)
   - Solder corner pads first to hold in place
   - Solder remaining pads using drag soldering technique
   - Check for bridges between pads with magnifier
   - Verify ground pad connection on bottom

### Step 4: Through-Hole Components

6. **DHT22 Sensor (U2)**
   - Insert through holes
   - Ensure sensor faces outward from PCB
   - Solder from bottom side
   - Trim excess leads

7. **Power Switch (SW1)**
   - Insert into mounting holes
   - Solder all pins
   - Check for smooth mechanical operation

8. **Battery Holder (BT1)**
   - Solder on bottom side of PCB
   - Ensure polarity markings are correct
   - Test mechanical fit with CR2032 battery (don't install yet)

9. **Optional: USB-C Connector (J1)**
   - Apply flux to all pads
   - Align connector carefully
   - Solder shield pins first
   - Then solder signal pins
   - Check all pins with multimeter for shorts

## Inspection and Cleaning

1. **Visual Inspection**:
   - Check all solder joints for quality
   - Look for solder bridges
   - Verify component orientation
   - Check for cold solder joints

2. **Cleaning**:
   - Remove flux residue with IPA and brush
   - Allow to dry completely
   - Inspect again after cleaning

## Initial Testing

### Power-On Test (WITHOUT Battery)

1. **Continuity Checks**:
   - VCC to GND: Should be open circuit (>1MΩ)
   - Check all power rails for shorts

2. **Power Supply Test** (if USB connector installed):
   - Connect USB cable
   - Measure 3.3V on ESP32 VCC pin
   - Verify current draw <50mA at idle

3. **Component Test**:
   - Touch EN pin to GND briefly (ESP32 should reset)
   - LED should light when powered

### Functional Test

4. **Sensor Communication**:
   - Program ESP32 with test firmware
   - Verify DHT22 responds on GPIO4
   - Check temperature reading is reasonable

5. **WiFi/BLE Test**:
   - Run WiFi scan in firmware
   - Check for BLE advertising
   - Verify no excessive current draw

6. **Battery Operation**:
   - Install CR2032 battery (observe polarity!)
   - Measure voltage at ESP32 VCC (should be ~3V)
   - Verify device operates normally
   - Check sleep mode current (<100μA)

## Common Issues and Troubleshooting

| Problem | Possible Cause | Solution |
|---------|----------------|----------|
| No power | Short circuit | Check VCC-GND with multimeter |
| ESP32 won't program | Not in boot mode | Hold GPIO0 low during reset |
| No WiFi | Poor solder on ESP32 | Reflow ESP32 module |
| DHT22 not responding | Bad connection | Check solder joints on pins |
| High current draw | Component shorted | Check for solder bridges |
| Battery drains fast | Not entering sleep | Check firmware power management |

## Final Quality Check

- [ ] All components properly soldered
- [ ] No solder bridges
- [ ] Correct component orientation
- [ ] PCB cleaned of flux
- [ ] Power-on test passed
- [ ] Functionality test passed
- [ ] Current consumption within spec
- [ ] Battery installed with correct polarity
- [ ] Mounting holes clear

## Safety Notes

⚠️ **Important Safety Information**:
- Use proper ventilation when soldering
- Wear safety glasses
- Use ESD protection for sensitive components
- CR2032 batteries can be dangerous if short-circuited
- Keep batteries away from children
- Dispose of batteries properly

## Programming

After assembly, the board needs to be programmed:
1. Connect via USB-C (if installed) or use Tag-Connect pogo pins
2. Hold GPIO0 button while pressing reset (or power on)
3. Use Arduino IDE or ESP-IDF to flash firmware
4. Release GPIO0 after programming starts

## Enclosure Assembly

1. Place assembled PCB in enclosure
2. Ensure sensor area has ventilation
3. Secure with M2.5 screws through mounting holes
4. Do not over-tighten screws (can crack PCB)

## Revision History

- **v1.0**: Initial assembly instructions
