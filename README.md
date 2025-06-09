NVNT's SDEX2M2 (MicroSD Express to M.2) Adapter Project

For creating an adapter to allow M.2 2230 SSD (NVME) drives to be used on the Nintendo Switch 2 utilizing the MicroSD Express Port.

🧠 How is this possible?

This is possible as the Nintendo Switch 2's MicroSD Express slot uses the SD Express 7.1 standard which supports a true PCIe Gen3 x1 interface, and utilizes the NVMe protocol for communication.

This adapter simply maps PCIe x1 from the Switch 2’s microSD slot to an M.2 2230 SSD (NVME). The adapter does not do any translation — it relies on the Switch 2’s host controller to handle everything.

🎯 Goals

Create Schematic: Necessary for PCB Design.

Create PCB Design with Gerber/Drill Files: The actual PCB design used.

Create BOM File: Necessary for production.

Offload VDD: As some drives may use more power, offloading VDD (Voltage/Power) to an external power source may be easier.

📦 Status

🚧 Work in progress. We are currently in development of the Gerber, Drill and other files necessary.

⚠️ Warnings:

- Use at your own risk! We are not liable for any damage caused to your M.2 NVMe Drive, Nintendo Switch 2 or other devices.
  
- To be used solely with low voltage M.2 NVMe 2230 Drives only
  
- Not to be used in traditional MicroSD card slots (such as those on Nintendo Switch 1) as it is not electronically compatible and may cause damage.
  
- This project is strictly for accesibility use. It may not be reproduced or used in commercial use, and is not intended to be used for illegal activities such as piracy.
