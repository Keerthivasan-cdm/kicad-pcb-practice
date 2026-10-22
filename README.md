# KiCad PCB Design Practice: ESP32-C3 Boards (Play U SMD)

Two practice boards designed in **KiCad 9** (Sep–Oct 2026): a full ESP32-C3 + 9-axis IMU wearable board, then a compact 4-layer revision of the MCU and battery section.

---

## Board 1: Play U SMD (v1), ESP32-C3 + ICM-20948 Wearable Board

**2-layer · 94.6 × 37.6 mm · 1.6 mm FR-4 · 77 footprints · 38 vias**

### Hierarchical schematic (3 sheets)
| Sheet | Contents |
|---|---|
| `ESP32C3.kicad_sch` | ESP32-C3-WROOM-02 module, USB-C 2.0 receptacle (5.1 kΩ CC pull-downs), **USBLC6-2SC6** USB ESD protection, **PESD5V0L1ULD** TVS, **AP2112K-3.3** 3.3 V LDO, crystal, RESET/BOOT buttons |
| `ICM_20948.kicad_sch` | **ICM-20948** 9-axis IMU (QFN-24), **TLV70018** 1.8 V LDO for the IMU core, I2C/SPI/aux bus pull-ups, decoupling |
| `ucharging and battery provisition.kicad_sch` | **BQ25185** single-cell Li-ion charger with power-path, **MAX16054** push-button on/off controller, charge/status LEDs, battery connector, power switch |

### Layout
- 0201 resistors and 0805 capacitors, QFN-24 IMU, SOT-23 regulators.
- Ground pours on both layers; 0.1–0.2 mm signal tracks.
- Design rules: 0.2 mm pad-to-pad and pad-to-track clearance, 0.1 mm minimum track width.
- **Fabrication outputs:** Gerbers (F/B copper, mask, paste, silkscreen, Edge.Cuts), PTH/NPTH drill files, Gerber job file, **STEP 3D model**.

---

## Board 2: ESP32-C3 Compact Battery Board (v2)

**4-layer · 28.6 × 42.1 mm · 46 footprints · 22 vias**

- Same MCU, USB-C/ESD and BQ25185 charging + MAX16054 power circuits, condensed into a single sheet (`esp32c3-compact-v2/esp32c3.kicad_sch`).
- 0402 passives, BOOT and RESET buttons, charge/status LEDs.
- Copper zones for **GND, VBUS, SYS and 3.3 V** power distribution.
- 0.15–0.4 mm track widths: wider for power, narrower for signals.

---

## Repository layout
```
play-u-smd-v1/            Board 1: open ESP_32.kicad_pro in KiCad 9
  ESP_32.kicad_sch        root sheet
  ESP32C3.kicad_sch       MCU + USB-C + LDO sheet
  ICM_20948.kicad_sch     IMU sheet
  ucharging and battery provisition.kicad_sch   charger + power sheet
  ESP_32.kicad_pcb        2-layer layout
  gerbers/                Gerber, drill and job files (ready for JLCPCB/PCBWay)
  3d/                     STEP 3D models
esp32c3-compact-v2/       Board 2: open esp32c3.kicad_pro
```

## Tools
KiCad 9.0 (Eeschema, Pcbnew, 3D viewer), custom symbols and footprints for ICM-20948, BQ25185, TLV70018 and MAX16054.

## Author
**Keerthivasan J**, B.E. EEE, Sri Sairam Engineering College ([GitHub](https://github.com/Keerthivasan-cdm) · [LinkedIn](https://linkedin.com/in/keerthi-vasan-j))
