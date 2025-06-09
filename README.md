# NVNT's SDEX2M2 (MicroSD Express to M.2) Adapter Project

> Adapter for using M.2 2230 NVMe SSDs in the Nintendo Switch 2 via the MicroSD Express port.

---

## 📚 Table of Contents

- [🧠 How is this possible?](#-how-is-this-possible)
- [🎯 Goals](#-goals)
- [📦 Status](#-status)
- [⚠️ Warnings](#️-warnings)
- [📋 Bill of Materials (BOM)](#-bill-of-materials-bom)
- [📌 PINOUT & LEGEND](#-pinout--legend)
  - [MicroSD Express ➝ M.2 NVMe Mapping](#microsd-express--m2-nvme-mapping)
  - [M.2 NVMe Pin Definitions](#m2-nvme-pin-definitions)
  - [MicroSD Express Pin Definitions](#microsd-express-pin-definitions)

---

## 🧠 How is this possible?

This is possible because the Nintendo Switch 2's MicroSD Express slot supports the SD Express 7.1 standard, which exposes a **true PCIe Gen3 x1 interface** and utilizes the **NVMe protocol** for communication.

This adapter simply maps PCIe x1 from the Switch 2’s MicroSD Express slot to a standard M.2 2230 NVMe SSD.  
No protocol translation is required — the Switch 2 host controller handles everything.

---

## 🎯 Goals

- ✅ Create Schematic for PCB layout
- ✅ Create routed PCB with Gerber/Drill files
- ✅ Create BOM for fabrication and sourcing
- ✅ (Optional) Offload VDD externally for higher-power drives

---

## 📦 Status

🚧 Work in progress.  
We are actively developing the PCB layout, manufacturing files, and 3D models.

---

## ⚠️ Warnings

- Use at your own risk. We are **not liable** for any damage to your drive, Switch 2, or other devices.
- Only use **low-voltage, low-power M.2 2230 NVMe drives**.
- **Do not use this in legacy MicroSD slots** (e.g., original Nintendo Switch).
- This project is for **accessibility/educational use only**.  
  No commercial or piracy use permitted.

---

## 📋 Bill of Materials (BOM)

| Reference | Quantity | Description                             | Part Number        | Manufacturer   |
|-----------|----------|-----------------------------------------|--------------------|----------------|
| J1        | 1        | MicroSD Express Edge Connector (TF 7.1) | Custom-19PIN-MSDX  | Generic/Custom |
| J2        | 1        | M.2 Socket (M-Key, 2230)                | 114020             | Amphenol       |
| C1        | 1        | Bypass Capacitor 0.1uF 0603             | GRM188R71C104KA01D | Murata         |
| C2        | 1        | Bypass Capacitor 1uF 0603               | CL10A105KB8NNNC    | Samsung        |
| FB1       | 1        | Ferrite Bead 220Ω@100MHz 0603           | BLM18PG221SN1D     | Murata         |
| PCB       | 1        | 4-Layer Impedance Controlled PCB        | N/A                | Fabricated     |

---

## 📌 PINOUT & LEGEND

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
| 13   | GND      | Ground                     |
| 14   | TX+      | PCIe TX (host ➝ device) +  |
| 15   | TX−      | PCIe TX (host ➝ device) −  |
| 16   | GND      | Ground                     |
| 17   | RX+      | PCIe RX (device ➝ host) +  |
| 18   | RX−      | PCIe RX (device ➝ host) −  |
| 19   | GND      | Ground                     |
