# NVNT's SDEX2M2 (MicroSD Express to M.2) Adapter Project

> Adapter for using M.2 2230 NVMe SSDs in the Nintendo Switch 2 via the MicroSD Express port.

---

## 📚 Table of Contents
- Introduction
  - [Goals](#goals)
  - [Status](#status)
  - [Warnings](#warnings)
- Assets & Hardware Info
  - [Bill of Materials (BOM)](#bill-of-materials-bom)
  - [PINOUT & LEGEND](#pinout--legend)
    - [MicroSD Express ➝ M.2 NVMe Mapping](#microsd-express--m2-nvme-mapping)
    - [M.2 NVMe Pin Definitions](#m2-nvme-pin-definitions)
    - [MicroSD Express Pin Definitions](#microsd-express-pin-definitions)
  - [Wiring Schematic](#wiring-schematic)
  - [MicroSD Express Dummy Card](#wiring-schematic)

---

## How is this possible?

This is possible because the Nintendo Switch 2's MicroSD Express slot supports the SD Express 7.1 standard, which exposes a **true PCIe Gen3 x1 interface** and utilizes the **NVMe protocol** for communication.

This adapter simply maps PCIe x1 from the Switch 2’s MicroSD Express slot to a standard M.2 2230 NVMe SSD. After further research and review from users, an onboard mcu will be required for the handshake provess with the Switch 2.

Currently, a MicroSD Express breakbout is being developed to start this process.

---

## Goals

- ✅ Create Pinout & Pin Definitions
- ✅ Create Footprints for MicroSD Express
- ✅ Create Schematic for PCB layout
- ✅ Create Dummy MicroSD Express Card
- 🔲 Create Dummy MicroSD Express card with breakout for prototyping
- 🔲 Create routed PCB with Gerber/Drill files
- ✅ Create BOM for fabrication and sourcing
- 🔲 (Optional) Offload VDD externally for higher-power drives
- 🔲 Produce & Test

---

## Status

Work in progress.  
We are actively developing the PCB layout, and testing.

There is still the possibility that there are power-related issues (ie: power draw of M.2 drives is more than the Switch 2 can push out), but a basic level of power filtering has been added to hopefully help a connection be established.

---

## Warnings

- Use at your own risk. We are **not liable** for any damage to your drive, Switch 2, or other devices.
- Only use **low-voltage, low-power M.2 2230 NVMe drives**.
- **Do not use this in legacy MicroSD slots** (e.g., original Nintendo Switch).
- This project is for **accessibility/educational use only**.  No commercial or piracy use permitted.

---

## Bill of Materials (BOM)

| Reference | Quantity | Description                             | Part Number        | Manufacturer   |
|-----------|----------|-----------------------------------------|--------------------|----------------|
| J2        | 1        | M.2 Socket (M-Key, 2230)                | 114020             | Amphenol       |
| FB1       | 1        | Ferrite Bead 220Ω@100MHz 0603           | BLM18PG221SN1D     | Murata/OEM     |
| PCB       | 1        | 4-Layer PCB        | N/A                | Fabricated         | *              |
|*          | 1        | 10kΩ – 100kΩ Pull Up Resistor (Optional) | N/A               | *              |

The optional resistor is for the PERST# lane, may help with state when idle. Not sure if needed until prototyping commences.

---

## PINOUT & LEGEND

### MicroSD Express ➝ M.2 NVMe Mapping

| MicroSD Express    | Signal     | M.2 NVMe Slot |
|--------------------|------------|---------------|
| 10                 | REFCLK+    | B10           |
| 11                 | REFCLK−    | B11           |
| 12                 | PERST#     | A11           |
| 14                 | TX+        | B23           |
| 15                 | TX−        | B24           |
| 17                 | RX+        | A21           |
| 18                 | RX−        | A22           |
| Row 1 Pin 4        | VDD (3.3V) | B2/B3/B4      |
| Pins 9, 13, 16, 19 | GND        | A1/A4/etc.    |

---

### M.2 NVMe Pin Definitions

| Pin     | Name     | Function                 |
|---------|----------|--------------------------|
| A11     | PERST#   | PCIe Reset               |
| A21     | RX+      | PCIe RX+ (to host)       |
| A22     | RX−      | PCIe RX− (to host)       |
| B10     | REFCLK+  | PCIe Reference Clock +   |
| B11     | REFCLK−  | PCIe Reference Clock −   |
| B23     | TX+      | PCIe TX+ (from host)     |
| B24     | TX−      | PCIe TX− (from host)     |
| B2–B4   | 3.3V     | Power Supply             |
| A1, A4  | GND      | Ground Pins              |

---

### MicroSD Express Pin Definitions

| Pin  | Name     | Function                   |
|------|----------|----------------------------|
| 9    | GND      | Ground                     |
| 10   | REFCLK+  | PCIe Reference Clock +     |
| 11   | REFCLK−  | PCIe Reference Clock −     |
| 12   | PERST#   | PCIe Reset                 |
| 14   | TX+      | PCIe TX (host ➝ device) +  |
| 15   | TX−      | PCIe TX (host ➝ device) −  |
| 17   | RX+      | PCIe RX (device ➝ host) +  |
| 18   | RX−      | PCIe RX (device ➝ host) −  |
| 19   | GND      | Ground                     |

---

### Wiring Schematic

![image](https://github.com/user-attachments/assets/24d717a2-7385-4293-a098-90bb4e63f5af)

Still a WIP. May not need the bead.

---

### MicroSD Express Dummy Card

As there is no footprint, dummy card or other files which could be useful to this project and other hardware hackers (at the time of writing), I have gone ahead and created them.

Please note, the Dummy Card is for reference only as no public information exists for the pin pitch. It requires tweaking. Will be updated asap.

![image](https://github.com/user-attachments/assets/22540149-7b47-4f09-8c33-7f98d65de4fb)


---
