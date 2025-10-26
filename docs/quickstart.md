# Quick Start Guide - Fridge Tag PCB

This guide will help you get started with your Fridge Tag PCB, from ordering to deployment.

## Step 1: Order PCBs

### Option A: Manufacturing Service

1. **Download Gerber files** from `hardware/gerbers/`
2. **Choose a manufacturer**:
   - JLCPCB (recommended for low-cost prototypes)
   - PCBWay (good quality, medium price)
   - OSH Park (premium quality, higher price)

3. **Upload Gerber files** to manufacturer's website
4. **Select specifications**:
   - Layers: 2
   - Thickness: 1.6mm
   - Surface finish: ENIG preferred
   - Color: Green (or your preference)
   - Quantity: 5-10 for prototypes

5. **Order and wait** (typically 1-2 weeks)

### Option B: DIY Fabrication (Not Recommended)

For simple prototypes, you could etch your own PCB, but this is not recommended for this design due to the fine pitch of the ESP32 module.

## Step 2: Order Components

### Quick BOM

Download the full BOM from `docs/BOM.md`. Main components:

| Component | Qty | Example Source |
|-----------|-----|----------------|
| ESP32-WROOM-32 | 1 | DigiKey, Mouser, AliExpress |
| DHT22 Sensor | 1 | DigiKey, Amazon, AliExpress |
| CR2032 Holder | 1 | DigiKey, Mouser |
| Resistors (0805) | 3 | DigiKey, Mouser |
| Capacitors (0805) | 2 | DigiKey, Mouser |
| LED (0805) | 1 | DigiKey, Mouser |
| Power Switch | 1 | DigiKey, Mouser |

**Total Cost**: ~$10-15 per unit (in small quantities)

### Component Kits

Some suppliers offer component kits for common projects. Check:
- Mouser project kits
- DigiKey BOM manager
- Arrow Electronics

## Step 3: Assembly

### Tools Needed

- Soldering iron (temperature controlled)
- Solder (lead-free recommended)
- Tweezers
- Magnifying glass
- Multimeter
- Flux

### Assembly Process

Follow the detailed instructions in `docs/assembly-instructions.md`.

**Quick Steps**:
1. Solder smallest components first (resistors, capacitors)
2. Solder ESP32 module (most critical - use flux!)
3. Solder LED and switch
4. Solder DHT22 sensor
5. Solder battery holder
6. Clean flux residue
7. Inspect all joints

**Time Required**: 30-60 minutes per board (for experienced assemblers)

## Step 4: Testing

### Basic Power Test

1. **DO NOT install battery yet**
2. Set multimeter to continuity mode
3. Check VCC to GND - should be open circuit
4. Check for shorts between adjacent pins

### Functional Test (with USB power if available)

1. Connect USB cable (if USB connector installed)
2. Measure voltage at ESP32 VCC pin (should be ~3.3V)
3. LED should light up

### Battery Installation

1. Verify polarity markings
2. Insert CR2032 battery (+ side up, typically)
3. Switch ON
4. Check LED illuminates

## Step 5: Programming

### Setup Development Environment

**Option A: Arduino IDE**

1. Install Arduino IDE from arduino.cc
2. Install ESP32 board support:
   - File → Preferences
   - Add to Additional Board Manager URLs:
     ```
     https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
     ```
   - Tools → Board → Boards Manager
   - Search "ESP32" and install

3. Install DHT sensor library:
   - Sketch → Include Library → Manage Libraries
   - Search "DHT sensor library" by Adafruit
   - Install both "DHT sensor library" and "Adafruit Unified Sensor"

**Option B: PlatformIO**

1. Install VS Code
2. Install PlatformIO extension
3. Create new project with ESP32 board

### Example Code

Create a simple test program:

```cpp
#include <DHT.h>

#define DHTPIN 4        // GPIO4
#define DHTTYPE DHT22   
#define LED_PIN 2       // GPIO2

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(115200);
  pinMode(LED_PIN, OUTPUT);
  dht.begin();
  Serial.println("Fridge Tag Starting...");
}

void loop() {
  // Blink LED
  digitalWrite(LED_PIN, HIGH);
  delay(100);
  digitalWrite(LED_PIN, LOW);
  
  // Read sensor
  float h = dht.readHumidity();
  float t = dht.readTemperature();
  
  if (isnan(h) || isnan(t)) {
    Serial.println("Failed to read from DHT sensor!");
    delay(2000);
    return;
  }
  
  Serial.print("Humidity: ");
  Serial.print(h);
  Serial.print("%  Temperature: ");
  Serial.print(t);
  Serial.println("°C");
  
  // Wait 5 seconds between readings
  delay(5000);
}
```

### Upload Code

1. Connect USB cable (or use Tag-Connect)
2. Select correct board: "ESP32 Dev Module"
3. Select correct port: /dev/ttyUSB0 (Linux) or COM3 (Windows)
4. Hold GPIO0 button while pressing reset (if no auto-reset)
5. Click Upload
6. Monitor Serial output

## Step 6: Deployment

### Enclosure

1. Design and 3D print an enclosure, or use a standard project box
2. Ensure sensor area has ventilation holes
3. Mount PCB with M2.5 screws
4. Don't overtighten (can crack PCB)

### Placement

1. Place in refrigerator away from direct cold air flow
2. Ensure wireless signal can reach outside
3. Test connectivity before final placement

### Monitoring

Set up your monitoring system:
- Configure WiFi credentials
- Set up MQTT broker or cloud service
- Configure alert thresholds
- Test notifications

## Troubleshooting

### Common Issues

**No power / LED doesn't light**
- Check battery polarity
- Check for solder bridges (VCC to GND short)
- Verify switch is ON

**Can't program ESP32**
- Check USB connection
- Try holding GPIO0 during power-on
- Verify correct COM port selected
- Check for driver issues (CP2102/CH340)

**Sensor reads NaN**
- Check DHT22 connections
- Verify pull-up resistor installed
- Try different GPIO pin in code
- Sensor may be defective

**High current drain**
- ESP32 not entering sleep mode
- Check for solder bridges
- Verify firmware implements deep sleep
- Measure current in sleep mode (<100μA)

**Poor WiFi range**
- Check antenna area (no copper)
- Ensure ground plane under ESP32
- Try different orientation
- Check for metal interference

## Next Steps

### Advanced Features

- Implement deep sleep for battery saving
- Add MQTT for data transmission
- Create web interface for configuration
- Add OTA firmware updates
- Integrate with Home Assistant or similar

### Customization

- Modify sensor reading intervals
- Add additional sensors
- Change LED behavior
- Customize enclosure design

## Resources

- **KiCad Documentation**: https://docs.kicad.org/
- **ESP32 Documentation**: https://docs.espressif.com/
- **DHT22 Datasheet**: Available from manufacturer
- **Community Forums**: ESP32 forum, KiCad forum

## Support

If you encounter issues:
1. Check documentation in `docs/` directory
2. Review schematic and PCB layout
3. Search existing GitHub issues
4. Create new issue with details

Happy building! 🎉
