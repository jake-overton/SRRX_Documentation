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

| Pin Number | Tortoise Internal Function      | CAT5 Wire Color    | Functional Group                       |
| :--------: | :------------------------------ | :----------------- | :------------------------------------- |
| **Pin 1**  | Motor Lead A                    | **Solid Blue**     | Motor Power                            |
| **Pin 2**  | Switch 1 (Normally Closed / NO) | **Solid Orange**   | Switch 1 Logic                         |
| **Pin 3**  | Switch 1 (Normally Open / NC)   | **Orange / White** | Switch 1 Logic                         |
| **Pin 4**  | **Switch 1 Common**             | **Solid Green**    | Switch 1 Common (Frog power when used) |
| **Pin 5**  | **Switch 2 Common**             | **Green / White**  | Switch 2 Common                        |
| **Pin 6**  | Switch 2 (Normally Open / NC)   | **Solid Brown**    | Switch 2 Logic                         |
| **Pin 7**  | Switch 2 (Normally Closed / NO) | **Brown / White**  | Switch 2 Logic                         |
| **Pin 8**  | Motor Lead B                    | **Blue / White**   | Motor Power                            |

#### B. Accessory Bus Color Assignment
* The main accessory bus will us Yellow (+) and White (-) 14AWG stranded silicone wire.
* The sub bus and feeders will use the 24AWG CAT5 wire. Since it is salvaged wire, some is stranded, some is solid core. (see Structure Lighting Standard above)

---

## 4. Turnout Control Sub-Panel (CSB1 / MCP23017 / DRV8833)
Intermediate sub-panel translating I2C commands from the CSB1 host into bi-directional 12V DC polarity for slow-motion Tortoise switch machines, allowing software throttle control (Engine Driver, JMRI, etc.) without toggle switches or track power dependency.

* **Capacity:** 2× MCP23017 16-bit I/O expanders (32 GPIO total) driving 5× DRV8833 dual H-bridge boards (2 Tortoise channels each). Supports up to 16 turnouts at full build-out; 10 initially configured across all 5 driver boards.
* **I2C Bus Addressing (confirmed):**
    * Board 1 (main/left): base address **0x20** — no address jumpers bridged.
    * Board 2 (right): **0x21** once the A0 jumper pad is bridged.
* **Logic Domain (3.3V):** Delivered from the CSB1 via a 4-conductor Qwiic/JST-SH link (3.3V, GND, SDA, SCL). The outer two pins on the MCP23017 breakout headers are unused pads, not active conductors.
    * *Gauge transition:* CSB1-side Qwiic conductors are ~28AWG; panel-side wiring runs ~18AWG. Connected via Dupont connectors.
* **Motor Domain (12V):** External 12V DC accessory supply landing on the infeed terminal block, daisy-chained to all 5 DRV8833 `VM`/`GND` pins via 24AWG Cat5e core: solid Orange = +12V (VM), Orange/White = common (GND).
* **Common Ground:** External 12V supply negative, DRV8833 ground bus, and CSB1/MCP logic ground are tied together at the infeed block — single-point reference across the 3.3V logic / 12V driver interface.
* **DRV8833 Sleep/Enable:** EEP jumper (backside of each DRV8833 board) bridged on all 5 boards to hold drive channels active/non-sleeping.
* **Logic & Motor Jumpers (MCP → DRV8833 → Terminal Strips):** Dupont ribbon jumpers. Colors are internally consistent per board (same pair used consistently for a given IN/OUT function on that board) but **not** globally consistent across all 5 boards — the ribbon color supply ran short partway through, so some boards substitute Gray/Purple and Blue/Green in place of the standard Brown/Red and Orange/Yellow pairs used elsewhere.
    * ⚠️ Do not assume a color = function mapping holds across boards. Per-board legend below to be completed as each board is finalized.
Note 9-2-26: I think the best way to run the 12VDC wires out of the panel to the tortoise would be to use the same accessory sub-bus scheme of wiring, orange/orange-white or brown/brown-white 24 AWG CAT5e wires to the tortoise wiring harness block.

| DRV8833 Board # | Turnouts Driven | IN1–IN4 Colors | OUT1–OUT4 Colors | Notes |
| :---: | :--- | :--- | :--- | :--- |
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |
| 4 | | | | |
| 5 | | | | |

---
