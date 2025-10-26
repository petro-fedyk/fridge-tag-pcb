# Fridge Tag PCB

A compact IoT device for monitoring temperature and humidity inside refrigerators with wireless connectivity.

![Version](https://img.shields.io/badge/version-1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-design-yellow)

## Overview

The Fridge Tag is a battery-powered sensor device designed to monitor environmental conditions inside refrigerators. It features:

- 🌡️ Temperature monitoring (-40°C to +80°C)
- 💧 Humidity monitoring (0-100% RH)
- 📡 WiFi and Bluetooth Low Energy connectivity
- 🔋 Long battery life (3-6 months on CR2032)
- 📦 Compact form factor (50mm x 30mm)

## Repository Structure

```
fridge-tag-pcb/
├── hardware/              # PCB design files
│   ├── fridge-tag.kicad_pro      # KiCad project file
│   ├── fridge-tag.kicad_pcb      # PCB layout
│   ├── fridge-tag.kicad_sch      # Schematic
│   ├── gerbers/                   # Gerber files for manufacturing
│   ├── libraries/                 # Custom component libraries
│   ├── pcb/                       # PCB-related files
│   └── schematic/                 # Schematic-related files
├── docs/                  # Documentation
│   ├── BOM.md                     # Bill of Materials
│   ├── design-spec.md             # Design specifications
│   └── assembly-instructions.md   # Assembly guide
├── fabrication/           # Manufacturing files
│   └── manufacturing-spec.md      # Fab specifications
└── README.md             # This file
```

## Key Components

- **ESP32-WROOM-32**: Main microcontroller with WiFi/BLE
- **DHT22**: Temperature and humidity sensor
- **CR2032**: Coin cell battery (220mAh)
- **SMD Components**: 0805 size resistors and capacitors

## Getting Started

### Prerequisites

- **KiCad 6.0+**: For viewing and editing PCB files
- **Gerber Viewer**: For reviewing manufacturing files (optional)

### Opening the Project

1. Clone this repository:
   ```bash
   git clone https://github.com/petro-fedyk/fridge-tag-pcb.git
   cd fridge-tag-pcb
   ```

2. Open KiCad and load the project:
   ```
   File → Open Project → hardware/fridge-tag.kicad_pro
   ```

3. View the schematic:
   ```
   Open Schematic Editor (Eeschema)
   ```

4. View the PCB layout:
   ```
   Open PCB Editor (Pcbnew)
   ```

## Documentation

- **[Bill of Materials](docs/BOM.md)**: Complete list of components
- **[Design Specification](docs/design-spec.md)**: Technical specifications and architecture
- **[Assembly Instructions](docs/assembly-instructions.md)**: Step-by-step assembly guide
- **[Manufacturing Spec](fabrication/manufacturing-spec.md)**: PCB fabrication requirements

## PCB Specifications

| Parameter | Value |
|-----------|-------|
| Board Size | 50mm x 30mm |
| Layers | 2 (Top/Bottom) |
| Thickness | 1.6mm |
| Copper Weight | 1 oz (35μm) |
| Surface Finish | ENIG |
| Solder Mask | Green |
| Min Track/Space | 0.2mm/0.2mm |

## Manufacturing

### Generating Gerber Files

1. Open the PCB in KiCad Pcbnew
2. File → Plot
3. Select required layers
4. Generate Gerber and drill files
5. Review in Gerber viewer
6. Zip files for manufacturer

### Recommended Manufacturers

- JLCPCB
- PCBWay
- OSH Park
- Seeed Studio

## Assembly

The board can be assembled using:
- **SMT Assembly**: Recommended for production quantities
- **Hand Soldering**: Suitable for prototypes (0805 components are hand-solderable)

See [Assembly Instructions](docs/assembly-instructions.md) for detailed steps.

## Firmware

The PCB is designed to work with ESP32 firmware. Recommended frameworks:
- **Arduino IDE**: Easy to get started
- **ESP-IDF**: Full featured development
- **PlatformIO**: Modern build system

Example firmware features:
- Deep sleep mode for power saving
- Periodic sensor readings (configurable interval)
- BLE advertising or WiFi data transmission
- OTA firmware updates

## Testing

After assembly:
1. Visual inspection
2. Continuity testing
3. Power-on test
4. Sensor functionality test
5. Wireless connectivity test
6. Battery life measurement

## Power Consumption

| Mode | Current | Duration |
|------|---------|----------|
| Deep Sleep | ~10μA | 95% of time |
| Sensor Read | ~20mA | 2 seconds |
| WiFi Transmit | ~80mA | 3 seconds |
| BLE Advertise | ~40mA | 1 second |

**Estimated Battery Life**: 3-6 months with readings every 5 minutes

## License

This project is open source. See LICENSE file for details.

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## Version History

- **v1.0** (Current): Initial design
  - ESP32-based design
  - DHT22 sensor integration
  - CR2032 battery power
  - 2-layer PCB

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Check existing documentation
- Review the schematic and PCB layout

## Acknowledgments

- ESP32 community for excellent documentation
- KiCad project for the amazing EDA tool
- Component manufacturers for datasheets

## Disclaimer

This is a prototype design. Use at your own risk. Always verify the design before manufacturing.

---

**Status**: Design Phase  
**Last Updated**: 2025-10-26  
**Maintainer**: petro-fedyk