# Chapter 4: Electrical Distribution & Turnout Infrastructure

## 4.1 System Overview & Philosophy
The Silver Ridge Railroad (SRRX) electrical infrastructure is engineered around a single core tenet: solve the problems this specific mountain-division layout actually has, rather than designing for multi-operator club complexity[cite: 10, 11].

* **Single Command Authority:** A single DCC-EX CSB1 command station (5A capacity) powers the entire railroad[cite: 5, 10, 11]. N-scale current draw across realistic operations (4–5 simultaneous locomotives) does not warrant secondary boosters or complex booster power districts[cite: 10, 11].
* **Passive Local Short Isolation:** Track faults are isolated using passive automotive dome lamps, protecting N-scale rolling stock and preventing track faults from shutting down the global command station[cite: 5, 10, 11].
* **Dedicated DC Accessory Isolation:** Slow-motion switch machines and structure lighting are powered from an isolated DC distribution bus, keeping the 5A DCC track budget dedicated strictly to traction and sound[cite: 4, 5, 11].

---

## 4.2 Power Distribution Architecture

### 4.2.1 Command Station & Track Bus (DCC)
* **DCC-EX CSB1 Station:** Delivers up to 5.0A global track capacity[cite: 5, 10, 11].
* **Master 4-Fuse Protection:** To protect the internal H-bridge driver of the CSB1 during DC-PWM locomotive testing, polarity transitions, and cross-track faults, all four output terminals (`-A`, `+A`, `-B`, `+B`) have inline **5A fast-acting fuses** installed immediately at the chassis[cite: 5].
* **Main Track Bus:** 14 AWG stranded parallel zip wire (Red = Rail A / Hot; Black = Rail B / Common)[cite: 5, 6, 11].
* **Track Feeders:** 22 AWG solid-core wire (Blue = Rail A, White = Rail B) dropped every 3–6 feet and at every spur lead[cite: 5, 6, 11].
* **Physical Separation:** The 14 AWG DCC track bus is routed strictly along the **south side** of the L-girder web to eliminate inductive noise coupling into DC lines[cite: 5, 11].

### 4.2.2 12V DC Accessory Bus & Regulated Sub-Buses
* **Primary Source:** Dedicated 12V DC, 3A switching wall adapter terminating into 2.1mm × 5.5mm screw-terminal barrel jacks[cite: 1, 5, 11].
* **Main Accessory Bus:** 14 AWG flexible silicone wire (Yellow = `+12V`, White = `-12V Common`), routed strictly along the **north side** of the L-girder web[cite: 5, 8, 9, 11].
* **Voltage Regulation Tiers:**
  * **8.0V DC (Turnout Motor Bus):** Stepped down from 12V via an LM2596 buck converter to supply the DRV8833 turnout driver panel[cite: 1, 3, 12]. Running Tortoise motors at 8V provides quiet, prototypical slow-motion movement and prevents continuous stall heat buildup[cite: 1, 12].
  * **5.0V / 3.3V DC (Lighting Sub-Buses):** Local buck converters tap the 12V bus via insulation-displacement T-taps to feed LED street lamps, crossing signals, and interior building lighting[cite: 1, 11, 12].
* **Diagnostic Monitoring:** Eight (8) digital voltmeter displays (2 each of 4 colors) are mounted on the fascia to track DC voltage health across sectors[cite: 1, 12].

### 4.2.3 Structure Quick-Disconnect Protocol
To eliminate under-table soldering when moving buildings or maintaining scenery:
* Structural interior LEDs use 32 AWG enameled magnet wire (Copper = Anode `+`; Silver/Tinned = Cathode `-`)[cite: 1, 5, 12].
* Spliced under the roof deck to 24 AWG CAT5 patch cable leads (Solid Color = `+`; Striped Color = `-`)[cite: 1, 5, 12].
* Leads drop through the subroadbed and terminate into a male 2.1mm screw-terminal barrel plug that seats into a matching female jack mounted beneath the benchwork[cite: 1, 12].

---

## 4.3 Track Power Districts & #1003 Short Circuit Protection

### 4.3.1 The #1003 Automotive Bulb Strategy
Rather than investing in costly electronic breakers (e.g., NCE EB1), the layout is divided into 8 active isolated zones protected by series-wired incandescent bulbs[cite: 5, 10, 11].

| Specification         | #1156 Bulb (HO Standard)  | #1003 Bulb (SRRX Standard) | Operational Impact                                                                                                                            |     |
| :-------------------- | :------------------------ | :------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------- | --- |
| **Rated Voltage**     | 12.8V                     | 12.8V                      | Standard automotive envelope[cite: 10, 11].                                                                                                   |     |
| **Lit Fault Current** | ~2.10 Amps                | **~0.94 Amps**             | **The Melt Limit:** Keeps fault heat below the threshold that melts N-scale Delrin truck sideframes or welds wheelsets to rail[cite: 10, 11]. |     |
| **Cold Resistance**   | ~0.6 Ω                    | ~1.2 Ω                     | Negligible track voltage drop during normal operation[cite: 10, 11].                                                                          |     |
| **CSB1 Interaction**  | Can trip global 5A limit  | Caps fault at ~1A          | The CSB1 internal DRV8874 never trips; unaffected zones stay fully powered[cite: 10, 11].                                                     |     |
| **Diagnostics**       | Blinding / Excessive Heat | Bright (12W)               | Instantly illuminates under the fascia to show the shorted zone; self-resets when cleared[cite: 10, 11].                                      |     |


Main DCC Bus (14 AWG Red) ───[Barrier Strip Pos 8]─── (#1003 Bulb) ───[Pos 7]─── Protected Zone Rail A Main DCC Bus (14 AWG Black) ─[Barrier Strip Pos 5]─── [Jumper Loop] ───[Pos 6]─── Protected Zone Rail B


![[SRRX 1003 Short Protection Wiring.jpg]] 
* **Audible Auxiliary Warning (Future Provision):** Light-Dependent Resistor (LDR) sensor boards positioned across from each #1003 lamp will trigger a shared piezo buzzer under the benchwork when any lamp strikes, providing an audible alarm without drawing on track power[cite: 10, 11]. ### 4.3.2 Protection Zone Map Both rails are gapped with insulated joiners at all zone boundaries[cite: 5, 10, 11]. 

![[Silver Ridge Railway V12-wiring.png]]

| Zone ID  | Geographic / Operational Boundary | Color Code | Protection Device | Operational Rationale                                                                 |
| :------: | :-------------------------------- | :--------- | :---------------: | :------------------------------------------------------------------------------------ |
|  **1**   | PVJ Yard Ladder & Helper Pocket   | Gray       |   1× #1003 Bulb   | Isolates intensive classification switching from the main[cite: 8, 9, 11, 13].        |
|  **2**   | Mine Spur & Switchbacks           | Brown      |   1× #1003 Bulb   | High-grade branch; includes former Smelter Spur (Zone 5 retired)[cite: 8, 9, 11, 13]. |
|  **3**   | North Mainline                    | Purple     |   1× #1003 Bulb   | PVJ throat north through mountain tunnel bores to south portals[cite: 8, 9, 11, 13].  |
|  **4**   | PVJ Industrial Spur               | Dark Pink  |   1× #1003 Bulb   | Warehouse and depot trackage off the mainline[cite: 8, 9, 11, 13].                    |
|  **6**   | South Mainline                    | Orange     |   1× #1003 Bulb   | South tunnel portals through gorge to Silver Ridge throat[cite: 8, 9, 11, 13].        |
|  **7**   | Timberline Lumber                 | Rose       |   1× #1003 Bulb   | Dedicated east leg industry spur[cite: 8, 9, 11, 13].                                 |
|  **8**   | Timberline Fuel Depot             | Blue       |   1× #1003 Bulb   | West wall hazmat spur[cite: 8, 9, 11, 13].                                            |
|  **9**   | Silver Ridge Siding               | Dark Green |   1× #1003 Bulb   | South terminal runaround and staging siding[cite: 8, 9, 11, 13].                      |
| **Prog** | Isolated Programming Track        | N/A        | CSB1 Service Out  | Air-gapped; fed directly from CSB1 Programming Track terminal[cite: 10, 11].          |

--- 
## 4.4 Turnout Control Sub-Panel (I2C Solid-State Architecture) 
### 4.4.1 Architectural Rationale 
Commercial stationary DCC decoders (e.g., NCE Switch-8, Digitrax DS64) listen to track DCC packets, consume track power, and cost significantly more per output channel[cite: 4]. 
The SRRX utilizes a bench-built solid-state interface coupling **MCP23017 I/O expanders** with **DRV8833 dual full-bridge motor drivers**[cite: 2, 4, 5]: 
* **Native VPIN Addressing:** Translates DCC-EX software commands directly over I2C hardware without packet delay or track bus clutter[cite: 4]. 
* **Zero Track Power Consumption:** Continuous stall motor current (~16 mA per Tortoise) is drawn strictly from the 8V accessory buck circuit[cite: 4, 5, 12]. 
* **High Density:** Drives 10 active turnouts across 5 boards (expandable to 16 channels) on a single compact sub-panel[cite: 2, 4, 12]. 
### 4.4.2 Sub-Panel Hardware Configuration 
* **I2C Host Link:** 4-wire Qwiic interface (3.3V, GND, SDA, SCL) from the CSB1 to Board 1[cite: 1, 2, 5, 12]. 
* **MCP23017 Expanders:** 
	* **Board 1 (Address `0x20`):** All address jumper pads bridged[cite: 1, 2, 3, 12]. 
	* **Board 2 (Address `0x21`):** Jumper pad **`A0` bridged**; `A1` and `A2` left open (offset +1)[cite: 3]. 
	* **DRV8833 Dual Drivers (5 Modules):** 
	* **Sleep Mode Override:** Rear solder jumper **`J2 / EEP`** is bridged on all 5 boards to permanently disable sleep mode and hold stall torque on switch points[cite: 1, 2, 5, 12]. 
	* The `ULT` pin remains floating/unconnected[cite: 5].
* **Power & Common Grounding:** 
	* External 8.0V DC positive lands on the panel infeed block and feeds the distribution bus bars connected to DRV8833 `VM` pins (Solid Orange)[cite: 1, 2, 3, 12]. 
	* External 8.0V return connects to DRV8833 `GND` pins (White/Orange)[cite: 2, 3]. 
* **Unified Common Tie:** The 8V power supply negative, DRV8833 ground bus, and CSB1 3.3V logic ground are all tied together at the infeed terminal block to establish a rock-solid common ground reference[cite: 1, 2, 3, 12]. 

![[Node board schematic.png]]
* ### 4.4.3 Pin Mapping & Dead-Terminal Remap Register 
* ⚠️ **Hardware Exception:** During bench commissioning, pins **PB0–PB3 on Board 1 (`0x20`)** were damaged by a transient short and rendered inoperative[cite: 1, 12]. These two channels were permanently remapped in `myAutomation.h` to pins **PA4–PA7 on Board 2 (`0x21`)**[cite: 1, 3, 12]. 
 
| Turnout | MCP Address | GPIO Pins Used | Driver Board | Channel Output | Wiring / Field Location |
| :---: | :---: | :---: | :---: | :---: | :--- |
| **#1** | `0x20` | PA0 / PA1 | DRV8833 #1 | OUT1 / OUT2 | PVJ Yard Lead[cite: 3] |
| **#2** | `0x20` | PA2 / PA3 | DRV8833 #1 | OUT3 / OUT4 | PVJ Yard Track 1[cite: 3] |
| **#3** | `0x20` | PA4 / PA5 | DRV8833 #2 | OUT1 / OUT2 | PVJ Yard Track 2[cite: 3] |
| **#4** | `0x20` | PA6 / PA7 | DRV8833 #2 | OUT3 / OUT4 | Helper Pocket[cite: 3] |
| **#5** | `0x20` | PB4 / PB5 | DRV8833 #3 | OUT1 / OUT2 | Industrial Lead A[cite: 3] |
| **#6** | `0x20` | PB6 / PB7 | DRV8833 #3 | OUT3 / OUT4 | Industrial Lead B[cite: 3] |
| **#7** | `0x21` | PA0 / PA1 | DRV8833 #4 | OUT1 / OUT2 | Mainline Crossover North[cite: 3] |
| **#8** | `0x21` | PA2 / PA3 | DRV8833 #4 | OUT3 / OUT4 | Mainline Crossover South[cite: 3] |
| **#9** | `0x21` | **PA4 / PA5** *(Remapped)* | DRV8833 #5 | OUT1 / OUT2 | PVJ RIP Spur[cite: 1, 3, 12] |
| **#10**| `0x21` | **PA6 / PA7** *(Remapped)* | DRV8833 #5 | OUT3 / OUT4 | Team Track[cite: 1, 3, 12] |
| *DEAD* | `0x20` | **PB0, PB1, PB2, PB3** | *RETIRED* | *DO NOT CONNECT* | *Floating / Inoperative*[cite: 1, 3, 12] |

---
## 4.5 Tortoise Switch Machine & Turnout Standards 
### 4.5.1 Workbench Pre-Wiring Standard 
Every Tortoise switch machine is pre-wired at the bench with an 8-conductor stranded CAT5 tail (9–10 inches) soldered to all edge pads and terminated into an 8-position barrier terminal strip[cite: 1, 5, 12]. All stranded conductor ends are fitted with **hex-crimped wire ferrules** to eliminate screw-shearing and stray strands[cite: 1, 12]. 

|  Pin  | Tortoise Internal Function | CAT5 Wire Color    | Functional Assignment                                            |
| :---: | :------------------------- | :----------------- | :--------------------------------------------------------------- |
| **1** | Motor Lead A               | **Solid Blue**     | Reversible 8V DC Motor Drive[cite: 1, 3, 12]                     |
| **2** | Aux Switch 1 (NO)          | **Solid Orange**   | Switch 1 Logic / Position Feedback[cite: 1, 5, 12]               |
| **3** | Aux Switch 1 (NC)          | **Orange / White** | Switch 1 Logic / Position Feedback[cite: 1, 5, 12]               |
| **4** | **Aux Switch 1 Common**    | **Solid Green**    | Frog Power Feed *(Left unwired on sprung Pecos)*[cite: 1, 5, 12] |
| **5** | **Aux Switch 2 Common**    | **Green / White**  | Aux Switch 2 Common[cite: 1, 5, 12]                              |
| **6** | Aux Switch 2 (NO)          | **Solid Brown**    | Switch 2 Logic / Interlock[cite: 1, 5, 12]                       |
| **7** | Aux Switch 2 (NC)          | **Brown / White**  | Switch 2 Logic / Interlock[cite: 1, 5, 12]                       |
| **8** | Motor Lead B               | **Blue / White**   | Reversible 8V DC Motor Drive[cite: 1, 3, 12]                     |
### 4.5.2 Peco Electrofrog Standards 
* **Actuation Wire:** Stock Tortoise throw wires are upgraded to stiff **.032" K&S Music Wire** to reliably overcome internal Peco over-center spring tension[cite: 5]. 
* **Frog Auxiliary Wiring:** Auxiliary contacts (Pins 2, 3, 4) remain **unwired** on sprung Peco turnouts[cite: 5]. The point rails provide electrical contact, eliminating short circuits caused by contact timing differences during slow motor travel[cite: 5]. 
* **Rail Gapping:** Insulated plastic rail joiners are installed on **both diverging frog rails** on every turnout without exception[cite: 5]. 
---
## 4.6 Master Wiring Specifications & Crimp Standards

| Circuit Application       | Wire Specification                 | Color Standard                   | Termination / Interconnect Standard                                                                             |
| :------------------------ | :--------------------------------- | :------------------------------- | :-------------------------------------------------------------------------------------------------------------- |
| **DCC Main Trunk**        | 14 AWG Parallel Zip Wire           | Red (Rail A) / Black (Rail B)    | Blue-insulated flanged spade crimps onto barrier strips[cite: 5, 6, 7, 11].                                     |
| **DCC Zone Sub-Buses**    | 14 AWG Parallel Zip Wire           | Red (Protected) / Black (Common) | In-line series loop through #1003 bayonet socket[cite: 5, 7, 11].                                               |
| **Track Feeder Drops**    | 22 AWG Solid Core                  | Blue (Rail A) / White (Rail B)   | Soldered directly to outside base of rail; dropped every 3–6 ft[cite: 5, 6, 11].                                |
| **12V DC Main Bus**       | 14 AWG Stranded Silicone           | Yellow (`+12V`) / White (`GND`)  | In-line insulation-displacement T-taps along north web[cite: 5, 8, 9, 11, 13].                                  |
| **Low-Voltage Sub-Buses** | 24 AWG CAT5 (Solid/Strand)         | Solid (`+`) / Striped (`-`)      | **Yellow T-tap $\rightarrow$ Red spade clamp $\rightarrow$ Hex-crimped ferrule**[cite: 1, 5, 8, 9, 11, 12, 13]. |
| **Structure Drops**       | 32 AWG Magnet $\rightarrow$ 24 AWG | Solid (`+`) / Striped (`-`)      | 2.1mm male/female screw-terminal barrel connectors[cite: 1, 5, 12].                                             |
| **Tortoise Pigtails**     | 24 AWG Stranded CAT5               | Master 8-Pin Color Code          | Hex-crimped ferrules into 8-position nylon barrier strip[cite: 1, 5, 12].                                       |


