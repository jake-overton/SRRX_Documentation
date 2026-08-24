# Silver Ridge Railroad: Electrical & Wiring Master Log

## 1. Accessory Power Architecture
The layout utilizes a dual-bus power distribution system derived from a primary 12V DC, 3A power supply brick. 

* **Main Power Feed:** 12V DC input runs through an array of male/female barrel connectors equipped with screw terminals for robust, solderless infrastructure connections.
* **Voltage Regulation:** Three (3) buck board step-down converters are utilized to drop the 12V main supply down to dedicated 3.3V / 5V lines for structural and accessory lighting.
* **Control Panel Monitoring:** Eight (8) digital voltmeter displays (2 each of 4 distinct colors) are available for mounting on the fascia to provide instant, color-coded visual tracking of power health across different accessory sectors.

---

## 2. Structure Lighting Standard (N-Scale)
To maintain structural mobility and eliminate under-benchwork soldering headaches, all illuminated buildings use a "Plug-and-Play" quick-disconnect protocol.

* **Conductor Conversion:** Ultra-thin 32 AWG enameled (magnet) wire from LEDs is extended down through the layout deck by splicing into 24 AWG stranded CAT5 patch cable conductors. 
    * *Polarity Coding:* The factory copper-colored wire designates the **Anode (+)**; the pre-tinned silver-colored wire designates the **Cathode (-)**.
    * *CAT5 Wire Matching:* Solid-colored CAT5 strands map to Positive (+); striped CAT5 strands map to Negative (-) (see color assignments below).
* **Interface:** Structure leads terminate into a male screw-terminal barrel plug, which seats into a matching female barrel jack secured beneath the benchwork. This allows any building to be cleanly unplugged and lifted off the deck for maintenance.

---

## 3. Tortoise Switch Machine Master Wiring Map
To maximize long-term layout reliability, every Tortoise machine is pre-wired at the workbench with all 8 pins active prior to under-deck installation. 

* **Harness Design:** An 8-conductor stranded CAT5 tail (approx. 9-10 inches) is soldered directly to the Tortoise circuit board pads at the bench. 
* **Termination:** The wire tail terminates into an 8-position nylon barrier terminal strip.
* **Strain Relief & Integrity:** Bare stranded wires are fitted with hex-crimped wire ferrules prior to insertion into the terminal block cylinders to prevent screw shearing and stranded wire escape.

### Master Pin-to-Color Code Assignment
#### A. Tortoise color assignment
The physical twisted pairs of the CAT5 cable are matched directly to the internal functional groupings of the Tortoise mechanisms to maintain visual organization under the bench.

| Pin Number | Tortoise Internal Function | CAT5 Wire Color | Functional Group |
| :---: | :--- | :--- | :--- |
| **Pin 1** | Motor Lead A | **Solid Blue** | Motor Power |
| **Pin 2** | Switch 1 (Normally Closed / NO) | **Solid Orange** | Switch 1 Logic |
| **Pin 3** | Switch 1 (Normally Open / NC) | **Orange / White** | Switch 1 Logic |
| **Pin 4** | **Switch 1 Common** | **Solid Green** | Switch 1 Common (Frog power when used) |
| **Pin 5** | **Switch 2 Common** | **Green / White** | Switch 2 Common |
| **Pin 6** | Switch 2 (Normally Open / NC) | **Solid Brown** | Switch 2 Logic |
| **Pin 7** | Switch 2 (Normally Closed / NO) | **Brown / White** | Switch 2 Logic |
| **Pin 8** | Motor Lead B | **Blue / White** | Motor Power |

#### B. Accessory Bus Color Assignment
* The main accessory bus will us Yellow (+) and White (-) 14AWG stranded silicone wire.
* The sub bus and feeders will use the 24AWG CAT5 wire. Since it is salvaged wire, some is stranded, some is solid core. (see Structure Lighting Standard above)

---
