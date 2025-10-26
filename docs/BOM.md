# Bill of Materials - Fridge Tag PCB v1.0

## Main Components

| Ref | Qty | Value | Description | Footprint | Manufacturer | Part Number |
|-----|-----|-------|-------------|-----------|--------------|-------------|
| U1 | 1 | ESP32-WROOM-32 | WiFi/BLE Module | ESP32-WROOM-32 | Espressif | ESP32-WROOM-32D |
| U2 | 1 | DHT22 | Temperature & Humidity Sensor | DHT22 | Aosong | AM2302 |
| BT1 | 1 | CR2032 | 3V Coin Cell Battery | CR2032 Holder | Various | CR2032 |
| C1 | 1 | 100nF | Decoupling Capacitor | 0805 | Various | - |
| C2 | 1 | 10uF | Bulk Capacitor | 0805 | Various | - |
| R1 | 1 | 10k | Pull-up Resistor | 0805 | Various | - |
| R2 | 1 | 10k | Pull-up Resistor | 0805 | Various | - |
| SW1 | 1 | SPST | Power Switch | SMD Switch | Various | - |
| LED1 | 1 | Green | Status LED | 0805 | Various | - |
| R3 | 1 | 330 | LED Current Limiting | 0805 | Various | - |

## Optional Components

| Ref | Qty | Value | Description | Footprint | Manufacturer | Part Number |
|-----|-----|-------|-------------|-----------|--------------|-------------|
| J1 | 1 | USB-C | Programming Interface | USB-C Connector | Various | - |
| U3 | 1 | AMS1117-3.3 | 3.3V Regulator | SOT-223 | Advanced Monolithic Systems | AMS1117-3.3 |

## PCB Specifications

- **Board Size**: 50mm x 30mm
- **Layer Count**: 2 layers (Top and Bottom)
- **Board Thickness**: 1.6mm
- **Copper Weight**: 1 oz (35μm)
- **Surface Finish**: ENIG (Electroless Nickel Immersion Gold)
- **Solder Mask Color**: Green
- **Silkscreen Color**: White

## Notes

1. All resistors and capacitors are 0805 size for easy hand soldering
2. ESP32 module includes integrated antenna
3. DHT22 sensor measures both temperature (-40 to 80°C) and humidity (0-100% RH)
4. CR2032 battery provides approximately 3-6 months of operation depending on usage
5. Optional USB-C connector for programming and charging
