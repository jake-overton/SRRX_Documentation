# Chapter 4: Electrical Distribution & Turnout Infrastructure

## 4.1 System Overview & Philosophy
The Silver Ridge Railroad (SRRX) electrical infrastructure is engineered around a single core tenet: solve the problems this specific mountain-division layout actually has, rather than designing for multi-operator club complexity.

* **Single Command Authority:** A single DCC-EX CSB1 command station (5A capacity) powers the entire railroad. N-scale current draw across realistic operations (4–5 simultaneous locomotives) does not warrant secondary boosters or complex booster power districts.
* **Passive Local Short Isolation:** Track faults are isolated using passive automotive dome lamps, protecting N-scale rolling stock and preventing track faults from shutting down the global command station.
* **Dedicated DC Accessory Isolation:** Slow-motion switch machines and structure lighting are powered from an isolated DC distribution bus, keeping the 5A DCC track budget dedicated strictly to traction and sound.

---

## 4.2 Power Distribution Architecture

### 4.2.1 Command Station & Track Bus (DCC)
* **DCC-EX CSB1 Station:** Delivers up to 5.0A global track capacity.
* **Master 4-Fuse Protection:** To protect the internal H-bridge driver of the CSB1 during DC-PWM locomotive testing, polarity transitions, and cross-track faults, all four output terminals (`-A`, `+A`, `-B`, `+B`) have inline **5A fast-acting fuses** installed immediately at the chassis.
* **Main Track Bus:** 14 AWG stranded parallel zip wire (Red = Rail A / Hot; Black = Rail B / Common).
* **Track Feeders:** 22 AWG solid-core wire (Blue = Rail A, White = Rail B) dropped every 3–6 feet and at every spur lead.
* **Physical Separation:** The 14 AWG DCC track bus is routed strictly along the **south side** of the L-girder web to eliminate inductive noise coupling into DC lines.

### 4.2.2 12V DC Accessory Bus & Regulated Sub-Buses
* **Primary Source:** Dedicated 12V DC, 3A switching wall adapter terminating into 2.1mm × 5.5mm screw-terminal barrel jacks.
* **Main Accessory Bus:** 14 AWG flexible silicone wire (Yellow = `+12V`, White = `-12V Common`), routed strictly along the **north side** of the L-girder web.
* **Voltage Regulation Tiers:**
  * **8.0V DC (Turnout Motor Bus):** Stepped down from 12V via an LM2596 buck converter to supply the DRV8833 turnout driver panel. Running Tortoise motors at 8V provides quiet, prototypical slow-motion movement and prevents continuous stall heat buildup.
  * **5.0V / 3.3V DC (Lighting Sub-Buses):** Local buck converters tap the 12V bus via insulation-displacement T-taps to feed LED street lamps, crossing signals, and interior building lighting.
* **Diagnostic Monitoring:** Eight (8) digital voltmeter displays (2 each of 4 colors) are mounted on the fascia to track DC voltage health across sectors.

### 4.2.3 Structure Quick-Disconnect Protocol
To eliminate under-table soldering when moving buildings or maintaining scenery:
* Structural interior LEDs use 32 AWG enameled magnet wire (Copper = Anode `+`; Silver/Tinned = Cathode `-`).
* Spliced under the roof deck to 24 AWG CAT5 patch cable leads (Solid Color = `+`; Striped Color = `-`).
* Leads drop through the subroadbed and terminate into a male 2.1mm screw-terminal barrel plug that seats into a matching female jack mounted beneath the benchwork.

---

## 4.3 Track Power Districts & #1003 Short Circuit Protection

### 4.3.1 The #1003 Automotive Bulb Strategy
Rather than investing in costly electronic breakers (e.g., NCE EB1), the layout is divided into 8 active isolated zones protected by series-wired incandescent bulbs.

| Specification         | #1156 Bulb (HO Standard)  | #1003 Bulb (SRRX Standard) | Operational Impact                                                                                                                            |     |
| :-------------------- | :------------------------ | :------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| **Rated Voltage**     | 12.8V                     | 12.8V                      | Standard automotive envelope.                                                                                                   |     |
| **Lit Fault Current** | ~2.10 Amps                | **~0.94 Amps**             | **The Melt Limit:** Keeps fault heat below the threshold that melts N-scale Delrin truck sideframes or welds wheelsets to rail. |     |
| **Cold Resistance**   | ~0.6 Ω                    | ~1.2 Ω                     | Negligible track voltage drop during normal operation.                                                                          |     |
| **CSB1 Interaction**  | Can trip global 5A limit  | Caps fault at ~1A          | The CSB1 internal DRV8874 never trips; unaffected zones stay fully powered.                                                     |     |
| **Diagnostics**       | Blinding / Excessive Heat | Bright (12W)               | Instantly illuminates under the fascia to show the shorted zone; self-resets when cleared.                                      |     |


Main DCC Bus (14 AWG Red) ───[Barrier Strip Pos 8]─── (#1003 Bulb) ───[Pos 7]─── Protected Zone Rail A Main DCC Bus (14 AWG Black) ─[Barrier Strip Pos 5]─── [Jumper Loop] ───[Pos 6]─── Protected Zone Rail B


![[SRRX 1003 Short Protection Wiring.jpg]] 
* **Audible Auxiliary Warning (Future Provision):** Light-Dependent Resistor (LDR) sensor boards positioned across from each #1003 lamp will trigger a shared piezo buzzer under the benchwork when any lamp strikes, providing an audible alarm without drawing on track power. ### 4.3.2 Protection Zone Map Both rails are gapped with insulated joiners at all zone boundaries. 

![[Silver Ridge Railway V12-wiring.png]]

| Zone ID  | Geographic / Operational Boundary | Color Code | Protection Device | Operational Rationale                                                                 |
| :------: | :-------------------------------- | :--------- | :---------------: | :------------------------------------------------------------------------------------ |
|  **1**   | PVJ Yard Ladder & Helper Pocket   | Gray       |   1× #1003 Bulb   | Isolates intensive classification switching from the main.        |
|  **2**   | Mine Spur & Switchbacks           | Brown      |   1× #1003 Bulb   | High-grade branch; includes former Smelter Spur (Zone 5 retired). |
|  **3**   | North Mainline                    | Purple     |   1× #1003 Bulb   | PVJ throat north through mountain tunnel bores to south portals.  |
|  **4**   | PVJ Industrial Spur               | Dark Pink  |   1× #1003 Bulb   | Warehouse and depot trackage off the mainline.                    |
|  **6**   | South Mainline                    | Orange     |   1× #1003 Bulb   | South tunnel portals through gorge to Silver Ridge throat.        |
|  **7**   | Timberline Lumber                 | Rose       |   1× #1003 Bulb   | Dedicated east leg industry spur.                                 |
|  **8**   | Timberline Fuel Depot             | Blue       |   1× #1003 Bulb   | West wall hazmat spur.                                            |
|  **9**   | Silver Ridge Siding               | Dark Green |   1× #1003 Bulb   | South terminal runaround and staging siding.                      |
| **Prog** | Isolated Programming Track        | N/A        | CSB1 Service Out  | Air-gapped; fed directly from CSB1 Programming Track terminal.          |

--- 
## 4.4 Turnout Control Sub-Panel (I2C Solid-State Architecture) 
### 4.4.1 Architectural Rationale 
Commercial stationary DCC decoders (e.g., NCE Switch-8, Digitrax DS64) listen to track DCC packets, consume track power, and cost significantly more per output channel. 
The SRRX utilizes a bench-built solid-state interface coupling **MCP23017 I/O expanders** with **DRV8833 dual full-bridge motor drivers**: 
* **Native VPIN Addressing:** Translates DCC-EX software commands directly over I2C hardware without packet delay or track bus clutter. 
* **Zero Track Power Consumption:** Continuous stall motor current (~16 mA per Tortoise) is drawn strictly from the 8V accessory buck circuit. 
* **High Density:** Drives 10 active turnouts across 5 boards (expandable to 16 channels) on a single compact sub-panel. 
### 4.4.2 Sub-Panel Hardware Configuration 
* **I2C Host Link:** 4-wire Qwiic interface (3.3V, GND, SDA, SCL) from the CSB1 to Board 1. 
* **MCP23017 Expanders:** 
	* **Board 1 (Address `0x20`):** All address jumper pads bridged. 
	* **Board 2 (Address `0x21`):** Jumper pad **`A0` bridged**; `A1` and `A2` left open (offset +1). 
	* **DRV8833 Dual Drivers (5 Modules):** 
	* **Sleep Mode Override:** Rear solder jumper **`J2 / EEP`** is bridged on all 5 boards to permanently disable sleep mode and hold stall torque on switch points. 
	* The `ULT` pin remains floating/unconnected.
* **Power & Common Grounding:** 
	* External 8.0V DC positive lands on the panel infeed block and feeds the distribution bus bars connected to DRV8833 `VM` pins (Solid Orange). 
	* External 8.0V return connects to DRV8833 `GND` pins (White/Orange). 
* **Unified Common Tie:** The 8V power supply negative, DRV8833 ground bus, and CSB1 3.3V logic ground are all tied together at the infeed terminal block to establish a rock-solid common ground reference. 

![[Node board schematic.png]]
* ### 4.4.3 Pin Mapping & Dead-Terminal Remap Register 
* ⚠️ **Hardware Exception:** During bench commissioning, pins **PB0–PB3 on Board 1 (`0x20`)** were damaged by a transient short and rendered inoperative. These two channels were permanently remapped in `myAutomation.h` to pins **PA4–PA7 on Board 2 (`0x21`)**. 
 
| Turnout | MCP Address | GPIO Pins Used | Driver Board | Channel Output | Wiring / Field Location |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **#1** | `0x20` | PA0 / PA1 | DRV8833 #1 | OUT1 / OUT2 | PVJ Yard Lead |
| **#2** | `0x20` | PA2 / PA3 | DRV8833 #1 | OUT3 / OUT4 | PVJ Yard Track 1 |
| **#3** | `0x20` | PA4 / PA5 | DRV8833 #2 | OUT1 / OUT2 | PVJ Yard Track 2 |
| **#4** | `0x20` | PA6 / PA7 | DRV8833 #2 | OUT3 / OUT4 | Helper Pocket |
| **#5** | `0x20` | PB4 / PB5 | DRV8833 #3 | OUT1 / OUT2 | Industrial Lead A |
| **#6** | `0x20` | PB6 / PB7 | DRV8833 #3 | OUT3 / OUT4 | Industrial Lead B |
| **#7** | `0x21` | PA0 / PA1 | DRV8833 #4 | OUT1 / OUT2 | Mainline Crossover North |
| **#8** | `0x21` | PA2 / PA3 | DRV8833 #4 | OUT3 / OUT4 | Mainline Crossover South |
| **#9** | `0x21` | **PA4 / PA5** *(Remapped)* | DRV8833 #5 | OUT1 / OUT2 | PVJ RIP Spur |
| **#10**| `0x21` | **PA6 / PA7** *(Remapped)* | DRV8833 #5 | OUT3 / OUT4 | Team Track |
| *DEAD* | `0x20` | **PB0, PB1, PB2, PB3** | *RETIRED* | *DO NOT CONNECT* | *Floating / Inoperative* |

---
## 4.5 Tortoise Switch Machine & Turnout Standards 
### 4.5.1 Workbench Pre-Wiring Standard 
Every Tortoise switch machine is pre-wired at the bench with an 8-conductor stranded CAT5 tail (9–10 inches) soldered to all edge pads and terminated into an 8-position barrier terminal strip. All stranded conductor ends are fitted with **hex-crimped wire ferrules** to eliminate screw-shearing and stray strands. 

|  Pin  | Tortoise Internal Function | CAT5 Wire Color    | Functional Assignment                                            |
| :---: | :------------------------- | :----------------- | :--------------------------------------------------------------- |
| **1** | Motor Lead A               | **Solid Blue**     | Reversible 8V DC Motor Drive                     |
| **2** | Aux Switch 1 (NO)          | **Solid Orange**   | Switch 1 Logic / Position Feedback               |
| **3** | Aux Switch 1 (NC)          | **Orange / White** | Switch 1 Logic / Position Feedback               |
| **4** | **Aux Switch 1 Common**    | **Solid Green**    | Frog Power Feed *(Left unwired on sprung Pecos)* |
| **5** | **Aux Switch 2 Common**    | **Green / White**  | Aux Switch 2 Common                              |
| **6** | Aux Switch 2 (NO)          | **Solid Brown**    | Switch 2 Logic / Interlock                       |
| **7** | Aux Switch 2 (NC)          | **Brown / White**  | Switch 2 Logic / Interlock                       |
| **8** | Motor Lead B               | **Blue / White**   | Reversible 8V DC Motor Drive                     |
### 4.5.2 Peco Electrofrog Standards 
* **Actuation Wire:** Stock Tortoise throw wires are upgraded to stiff **.032" K&S Music Wire** to reliably overcome internal Peco over-center spring tension. 
* **Frog Auxiliary Wiring:** Auxiliary contacts (Pins 2, 3, 4) remain **unwired** on sprung Peco turnouts. The point rails provide electrical contact, eliminating short circuits caused by contact timing differences during slow motor travel. 
* **Rail Gapping:** Insulated plastic rail joiners are installed on **both diverging frog rails** on every turnout without exception. 
---
## 4.6 Master Wiring Specifications & Crimp Standards

| Circuit Application       | Wire Specification                 | Color Standard                   | Termination / Interconnect Standard                                                                             |
| :------------------------ | :--------------------------------- | :------------------------------- | :-------------------------------------------------------------------------------------------------------------- |
| **DCC Main Trunk**        | 14 AWG Parallel Zip Wire           | Red (Rail A) / Black (Rail B)    | Blue-insulated flanged spade crimps onto barrier strips.                                     |
| **DCC Zone Sub-Buses**    | 14 AWG Parallel Zip Wire           | Red (Protected) / Black (Common) | In-line series loop through #1003 bayonet socket.                                               |
| **Track Feeder Drops**    | 22 AWG Solid Core                  | Blue (Rail A) / White (Rail B)   | Soldered directly to outside base of rail; dropped every 3–6 ft.                                |
| **12V DC Main Bus**       | 14 AWG Stranded Silicone           | Yellow (`+12V`) / White (`GND`)  | In-line insulation-displacement T-taps along north web.                                  |
| **Low-Voltage Sub-Buses** | 24 AWG CAT5 (Solid/Strand)         | Solid (`+`) / Striped (`-`)      | **Yellow T-tap $\rightarrow$ Red spade clamp $\rightarrow$ Hex-crimped ferrule**. |
| **Structure Drops**       | 32 AWG Magnet $\rightarrow$ 24 AWG | Solid (`+`) / Striped (`-`)      | 2.1mm male/female screw-terminal barrel connectors.                                             |
| **Tortoise Pigtails**     | 24 AWG Stranded CAT5               | Master 8-Pin Color Code          | Hex-crimped ferrules into 8-position nylon barrier strip.                                       |


