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

| Specification | #1156 Bulb (HO Standard) | #1003 Bulb (SRRX Standard) | Operational Impact |
| :--- | :--- | :--- | :--- |
| **Rated Voltage** | 12.8V | 12.8V | Standard automotive envelope[cite: 10, 11]. |
| **Lit Fault Current** | ~2.10 Amps | **~0.94 Amps** | **The Melt Limit:** Keeps fault heat below the threshold that melts N-scale Delrin truck sideframes or welds wheelsets to rail[cite: 10, 11]. |
| **Cold Resistance** | ~0.6 Ω | ~1.2 Ω | Negligible track voltage drop during normal operation[cite: 10, 11]. |
| **CSB1 Interaction** | Can trip global 5A limit | Caps fault at ~1A | The CSB1 internal DRV8874 never trips; unaffected zones stay fully powered[cite: 10, 11]. |
| **Diagnostics** | Blinding / Excessive Heat | Bright (12W) | Instantly illuminates under the fascia to show the shorted zone; self-resets when cleared[cite: 10, 11]. |