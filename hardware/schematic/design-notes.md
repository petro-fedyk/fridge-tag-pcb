# Schematic Design Notes

## Circuit Description

### Power Supply Section

The power supply section provides stable 3.3V to all components:

```
Battery (CR2032) → SW1 (Power Switch) → VCC Rail (3.3V)
                                      ↓
                                    C2 (10µF) ← Bulk capacitor
                                      ↓
                                    ESP32, DHT22, LED
```

Alternative with USB power:
```
USB-C (J1) → AMS1117-3.3 → VCC Rail (3.3V)
```

### ESP32 Section

The ESP32-WROOM-32 is the main microcontroller:
- Pin connections:
  - GPIO4: DHT22 data line (with 10kΩ pull-up)
  - GPIO2: Status LED (with 330Ω current limiting resistor)
  - GPIO0: Boot mode select (pull-up to VCC)
  - EN: Enable/Reset (pull-up to VCC)
  - VCC: 3.3V power
  - GND: Ground

### Sensor Section

DHT22 Temperature/Humidity Sensor:
- VCC: 3.3V power
- Data: Single-wire digital interface to ESP32 GPIO4
- GND: Ground

Pull-up resistor (10kΩ) on data line ensures proper logic levels.

### Status Indicator

LED circuit:
```
GPIO2 → R3 (330Ω) → LED1 (Green) → GND
```

LED indicates:
- Solid ON: Device powered and active
- Blinking: Normal operation with periodic sensor reads
- OFF: Deep sleep mode or power off

### Decoupling

All ICs have local decoupling capacitors:
- C1 (100nF): High-frequency noise filtering
- C2 (10µF): Bulk capacitance for current spikes

## Design Considerations

### Low Power Design

1. **Sleep Modes**: ESP32 can enter deep sleep (10µA) between readings
2. **Sensor Power**: DHT22 draws minimal current in standby
3. **LED Control**: LED can be disabled in firmware to save power

### RF Performance

1. **Antenna Clearance**: 5mm keepout zone around ESP32 antenna
2. **Ground Plane**: Solid ground on bottom layer
3. **No Copper Pour**: Under ESP32 antenna area

### Signal Integrity

1. **Short Traces**: Keep critical signals short
2. **Pull-ups**: Ensure proper logic levels on I/O pins
3. **Decoupling**: Caps placed close to IC power pins

### Thermal Considerations

1. **Sensor Placement**: DHT22 away from heat sources
2. **Airflow**: PCB design allows natural convection
3. **Power Dissipation**: Minimal heat generation (<100mW typical)

## Component Selection Rationale

### ESP32-WROOM-32
- Integrated WiFi and BLE
- Low power modes
- Adequate GPIO for sensors
- Built-in antenna
- Large community support

### DHT22
- Accurate measurements (±0.5°C, ±2% RH)
- Digital output (no ADC needed)
- Wide operating range
- Low cost
- Single-wire interface

### CR2032 Battery
- Common and readily available
- 3V nominal (compatible with ESP32)
- 220mAh capacity
- Good low-temperature performance
- Long shelf life

### 0805 Components
- Hand-solderable
- Good availability
- Cost effective
- Adequate power rating

## Recommended Improvements for v2.0

1. Add accelerometer for door-open detection
2. Include battery voltage monitoring circuit
3. Add NFC for easy configuration
4. Consider rechargeable LiPo option
5. Add e-ink display for local reading
6. Include light sensor
7. Add buzzer for alarms
