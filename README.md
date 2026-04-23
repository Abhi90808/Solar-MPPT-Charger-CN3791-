# Solar MPPT Charger (CN3791)

A solar Li-ion battery charger PCB using the CN3791 MPPT IC, designed in KiCad 8. Optimized for single-cell Li-ion charging from small solar panels with automatic maximum power point tracking.

---

## Features
- CN3791 MPPT solar charging IC
- Single-cell Li-ion / Li-Po charging (4.2V)
- MPPT for maximum solar panel efficiency
- Charging current up to 2A (adjustable)
- Charge status LED indicator
- Compact SMD design

## Specifications

| Parameter | Value |
|-----------|-------|
| Charging IC | CN3791 |
| Solar Input Voltage | 4.5V – 6.5V (typical 5V panel) |
| Battery Type | Single-cell Li-ion / Li-Po |
| Charge Voltage | 4.2V |
| Max Charge Current | 2A (set by RPROG) |
| MPPT | Yes (resistor-programmable) |
| Efficiency | Up to 90% |
| PCB Layers | 2 |
| Designed With | KiCad 8 |

## Project Structure

```
├── Schematic/       # KiCad schematic (.kicad_sch, PDF)
├── PCB/             # PCB layout (.kicad_pcb, .kicad_pro)
├── Gerbers/         # Fabrication files
├── BOM/             # Bill of materials (CSV)
├── 3D/              # 3D model (.step)
└── Images/          # PCB renders and schematic screenshots
```

## How It Works

The CN3791 tracks the solar panel's maximum power point using a resistor-set voltage reference on the MPPT pin. It implements CC/CV charging — constant current until the battery reaches 4.2V, then switches to constant voltage. This ensures the solar panel always operates near its peak power output regardless of battery state.

## MPPT Voltage Setting

The MPPT input voltage is set by a resistor divider on the MPPT pin:

```
V_MPPT = 1.205 × (1 + R1/R2)
```

For a 5V panel with ~4.5V MPP: use R1 = 270kΩ and R2 = 100kΩ.

## Bill of Materials (Summary)

| Component | Value | Qty |
|-----------|-------|-----|
| MPPT Charger IC | CN3791 | 1 |
| Inductor | 10µH | 1 |
| Schottky Diode | SS14 | 1 |
| Input Capacitor | 10µF / 10V | 1 |
| Output Capacitor | 47µF / 10V | 1 |
| RPROG Resistor | 3.9kΩ (500mA) | 1 |
| MPPT Resistors | 270kΩ, 100kΩ | 2 |
| LED | Green | 1 |

## Fabrication

Gerber files are in `/Gerbers`, ready for JLCPCB, PCBWay, or similar.

## License

This project is licensed under the [CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN OHL-S v2)](https://ohwr.org/cern_ohl_s_v2.txt).

## Author

**Abhi90808** — [GitHub Profile](https://github.com/Abhi90808)
