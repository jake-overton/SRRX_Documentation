# 1. Power Supply & Command Infrastructure

- **Command Station:** **DCC-EX CSB1** integrated command station/booster providing up to $5\text{A}$ global capacity.
- **DC-PWM (Initial Testing Phase):** Configured via DCC-EX TrackManager for initial layout construction, track-testing, and running vintage DC locomotives safely without burning out DC motors.
- **CSB1 Master 4-Fuse Protection:**
 - To protect the CSB1's internal $H$-bridge driver during DC-PWM polarity switching and cross-track faults, **all four output terminals ($-A$, $+A$, $-B$, $+B$) must have an inline 5A fuse** installed immediately at the command station output.
- **Dedicated DC Accessory Supply:** A separate **12VDC, 3A power supply brick** powers all Tortoise switch machines and baseline layout lighting.
- **Physical Bus Separation:** * The **14 AWG Red/Black DCC Track Bus** runs along the **south side** of the L-girder web.
	- The **14 AWG Yellow/White 12VDC Accessory Bus** runs along the **north side** of the L-girder web to completely eliminate crosstalk and inductive interference.
# 2. Track Power & Short Protection
#### (#1003 Bulb Strategy)
- **Current Limiting Architecture:** The layout is divided into 8 active isolated track districts.   
- **#1003 Automotive Bulbs:**
    - Wired **strictly in series on Rail A (Hot Rail)** of each zone sub-bus terminal block.
    - Common Rail B (Black wire) remains continuous and uninterrupted.
    - **Thermal & Component Safety:** The #1003 bulb chokes short-circuit current to $\sim0.94\text{A}$ (12W), preventing melted N-scale Delrin tie strips or spot-welded wheelsets while keeping current well under the CSB1's 5A trip limit.
    - **Self-Resetting Diagnostics:** The illuminated bulb provides an instant visual fault indicator at the benchwork edge and extinguishes automatically when the short clears.
# 3. Wire Gauges & Color Coding Standards

| **Bus / Circuit Tier**     | **Line A / Positive (+)** | **Line B / Negative (-) / Common** | **Conductor Spec**                      | **Notes / Interconnects**                    |
| -------------------------- | ------------------------- | ---------------------------------- | --------------------------------------- | -------------------------------------------- |
| **DCC Main Trunk**         | 🔴 Red                    | ⚫ Black                            | 14 AWG Zip Wire                         | From CSB1 (via 5A fuses) down south L-girder |
| **Zone Sub-Buses**         | 🔴 Red (Protected)        | ⚫ Black                            | 14 AWG Zip Wire                         | Downstream of #1003 bulb block               |
| **Track Feeder Drops**     | 🔵 Blue                   | ⚪ White                            | 22 AWG Solid Core                       | Dropped every 3–6 ft & at district leads     |
| **12VDC Main Accessory**   | 🟡 Yellow                 | ⚪ White                            | 14 AWG Flexible Silicone                | Runs along north L-girder web                |
| **Structure Lighting LED** | Solid CAT5 Color          | Striped CAT5 Color                 | 32 AWG Magnet $\rightarrow$ 24 AWG CAT5 | Copper (Anode/+) / Silver (Cathode/-)        |
| **Low-Voltage Sub-Buses**  | Orange / Brown            | Orange-Wht / Brown-Wht             | 24 AWG LAN Cable                        | Step-downs via local buck boards (3.3V/5V)   |

- **Crimping Standard:** T-taps connecting 14 AWG main lines to 24 AWG CAT5 lines require a yellow tap and red spade. All stranded 24 AWG LAN wires must be **hex/square-crimped with ferrules** before insertion into spade clamps or nylon terminal strips.
# 4. Turnout Mechanics & Tortoise Switch Machines
- **Vintage Peco Electrofrogs:**
    - Sealed, inaccessible over-center internal springs.
    - **Actuation Wire:** Upgraded to **.032" K&S Music Wire** to overcome internal spring tension cleanly.
    - **Frog Contacts (Pins 3, 4, 5):** **Left unwired** for Peco turnouts with intact springs to eliminate momentary DCC bus shorts during the slow 2-second stall motor throw.
    - **Gapping:** Insulated plastic rail joiners are installed on **both inner frog rails** of every turnout.
- **Tortoise 8-Pin Edge Connector CAT5 Mapping:**
	- **Pins 1 & 8 (Motor Power):** Solid Blue & Blue / White
    - **Pins 2 & 3 (Aux Switch 1 Logic):** Solid Orange & Orange / White
    - **Pin 4 (Aux Switch 1 Common):** Solid Green
    - **Pins 6 & 7 (Aux Switch 2 Logic):** Solid Brown & Brown / White
    - **Pin 5 (Aux Switch 2 Common):** Green / White
    - Pre-wired at the workbench with CAT5 pigtails terminating into 8-position barrier terminal blocks.
# 5. PVJ Yard Turnout Automation Node
#### (I2C Solid-State Architecture)
- **Layout Turnout Distribution:**
    - **PVJ Yard (10 Turnouts):** Automated via DCC-EX CSB1 over an I2C Solid-State Node for Engine Driver & JMRI throttle/route alignment.
    - **Silver Ridge Mine Branch (3 Turnouts):** Manual local control via DPDT toggle switches on the fascia, matching the slow, deliberate pace of the switchback run.
    - **Silver Ridge Town (4 Turnouts):** Manual or local control on the accessible south front fascia.
- **The Accessory Switch Node (Bench-Built Chassis):**
    - **1× I2C Bus Trunk:** 4-wire shielded cable (3.3V, GND, SDA, SCL) connects the CSB1's Qwiic/STEMMA QT port to the yard node.
    - **2× MCP23017 16-bit I/O Expanders:**
        - _Board 1:_ Address `0x20` (default) $\rightarrow$ DCC-EX VPINs 100–115 (drives Turnouts 1–8).
        - _Board 2:_ Address `0x21` ($A0$ pad bridged) $\rightarrow$ DCC-EX VPINs 116–131 (drives Turnouts 9–10 + expansion).
    - **5× DRV8833 Dual H-Bridge Drivers (from 8-pack):**
        - Each DRV8833 drives **2 independent Tortoises** on continuous $12\text{VDC}$ polarity-reversed stall current ($\sim16\text{ mA}$ each).
        - **`J2` Solder Pad:** Bridged with solder on the back of each board to pull `EEP` (Sleep/Enable) HIGH permanently.
        - **Pins `IN1`/`IN2` & `IN3`/`IN4`:** Receive 3.3V logic signals from MCP23017 outputs.
        - **Pins `OUT1`/`OUT2` & `OUT3`/`OUT4`:** Connect directly to Tortoise Pins 1 & 8.
        - **`ULT` Pin:** Left unconnected (floating).
    - **Common Grounding:** CSB1 logic Ground and 12VDC Accessory Power Ground are tied together at the Node Board ground rail to ensure stable digital switching.