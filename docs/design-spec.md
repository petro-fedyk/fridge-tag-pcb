# Fridge Tag PCB Design Documentation

## Overview

The Fridge Tag is a compact IoT device designed to monitor temperature and humidity inside refrigerators. It features wireless connectivity for remote monitoring and is powered by a coin cell battery for long-term operation.

## Features

- **Temperature Monitoring**: -40°C to +80°C range
- **Humidity Monitoring**: 0-100% RH
- **Wireless Connectivity**: WiFi and Bluetooth Low Energy (BLE)
- **Low Power**: Optimized for battery operation
- **Compact Size**: 50mm x 30mm footprint
- **Easy Assembly**: Uses common SMD components (0805 size)

## System Architecture

### Main Components

1. **ESP32-WROOM-32**: Main microcontroller with integrated WiFi and BLE
   - Handles sensor data collection
   - Manages wireless communication
   - Implements low-power modes

2. **DHT22 Sensor**: Combined temperature and humidity sensor
   - Digital output via single-wire interface
   - ±0.5°C temperature accuracy
   - ±2% RH humidity accuracy

3. **Power System**:
   - CR2032 coin cell battery (3V, 220mAh typical)
   - Optional USB-C for programming/development
   - AMS1117-3.3 regulator for stable 3.3V supply

## Design Specifications

### Electrical

- **Operating Voltage**: 2.2V - 3.6V
- **Current Consumption**:
  - Deep Sleep: ~10μA
  - Active (WiFi): ~80mA (peak)
  - Active (BLE): ~40mA (peak)
- **Battery Life**: 3-6 months (typical usage pattern)

### Mechanical

- **PCB Dimensions**: 50mm x 30mm x 1.6mm
- **Mounting**: 4x M2.5 mounting holes
- **Enclosure**: Compatible with standard project boxes

### Environmental

- **Operating Temperature**: -20°C to +60°C
- **Storage Temperature**: -40°C to +85°C
- **Humidity**: 0-95% RH (non-condensing)

## Pin Assignments

### ESP32 Connections

| ESP32 Pin | Function | Connected To |
|-----------|----------|--------------|
| GPIO4 | DHT22 Data | U2 Data Pin |
| GPIO2 | Status LED | LED1 |
| GPIO0 | Boot Mode | Button/Pull-up |
| EN | Enable | Pull-up |
| 3V3 | Power Out | DHT22 VCC |
| GND | Ground | Common Ground |

### DHT22 Sensor

| Pin | Function | Connected To |
|-----|----------|--------------|
| 1 | VCC | 3.3V |
| 2 | Data | GPIO4 (with 10k pull-up) |
| 3 | NC | Not Connected |
| 4 | GND | Ground |

## Layout Guidelines

1. **Power Distribution**:
   - Keep power traces at least 0.5mm wide
   - Use ground plane on bottom layer
   - Place decoupling caps close to IC power pins

2. **RF Considerations**:
   - Keep ESP32 antenna area clear (no copper pour)
   - Maintain 5mm keepout zone around antenna
   - Route critical signals away from antenna

3. **Sensor Placement**:
   - Position DHT22 away from heat-generating components
   - Ensure good airflow to sensor area
   - Consider adding ventilation holes in enclosure

## Manufacturing Notes

- **Gerber Files**: Located in `/hardware/gerbers/`
- **Assembly**: Standard SMT assembly process
- **Testing**: Functional test fixture recommended
- **Programming**: Use USB-C or Tag-Connect pogo pins

## Firmware Requirements

The PCB is designed to work with firmware that implements:
- Low-power sleep modes
- Periodic sensor readings (e.g., every 5 minutes)
- BLE advertising or WiFi data transmission
- Battery voltage monitoring

## Version History

- **v1.0** (Current): Initial design release
  - ESP32-WROOM-32 based
  - DHT22 sensor
  - CR2032 battery power
  - 2-layer PCB

## Future Improvements

- Add e-ink display for local reading
- Implement rechargeable LiPo battery option
- Add accelerometer for door open/close detection
- Include NFC for easy pairing
