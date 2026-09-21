### Overview & Purpose

This assembly serves as an intermediate **Turnout Control Sub-Panel** for the layout. It interfaces between the layout command bus (via a CSB1 interface running I2C/Qwiic) and up to **16 slow-motion switch machines (Tortoise motors)** of which only 10 are initially configured.

This allows for a throttle (Engine Driver, JMRI or others) to control the turnouts in software without having to use toggle switches or manually throw the switch. It also does not rely on track power to run.

Its primary function of the panel is to translate low-voltage digital I2C logic commands into the bi-directional 8 VDC polarity shifts required to drive and stall slow-motion turnout motors in either the "Normal" or "Reverse" position.
[[Is This Better Than Commercially Available Decoders]]?

This is a picture of the schematic for wiring. 
- NOTE: The pins PB0-PB3 on the first board (0x20) proved unreliable (likely damaged in testing) so were rerouted to pins PA4-PA7 on the second board (0x21)

![[Node board schematic.png]]

### Key Components & Functions
- **2× MCP23017 16-Bit I/O Expanders (Qwiic / I2C):**
    - **Function:** Act as the digital interface for the board. They receive serial turnout commands over the 4-wire I2C bus (SDA/SCL) and translate them into 32 discrete digital output pins (GPA0–GPA7, GPB0–GPB7 on each board).
    - **Addressing:**
        - Board 1: Base address (all jumpers closed, default  `0x20`).
        - Board 2: Offset address via hardware solder bridge across the **A1 and A2 jumper pads, leaving A0 open, (e.g.,  `0x21`) using a 28 AWG wire bridge.
- **5× DRV8833 Dual H-Bridge Motor Driver Boards:**
    - **Function:** Act as the high-power polarity switches. Each DRV8833 module contains two independent full H-bridges (handling 2 switch machines per board, for a total capacity of 10 turnouts across the 5 boards).
    - **Operation:** Receives 3.3V logic signals from the MCP23017 pins (`IN1`/`IN2`, `IN3`/`IN4`) and routes 8V DC motor current to the output pins with reversible polarity (`OUT1`/`OUT2`, `OUT3`/`OUT4`).
    - **Configuration:** Sleep mode (`EEP` / `J2`) jumper pads are permanently bridged on the underside with copper wire to keep driver channels active and holding stall current.
- **10× 2-Pole Screw Terminal Blocks:**
    - **Function:** Field wiring breakout points located along the baseboard edge, securing the field wiring runs out to the Tortoise switch motors.
- **1× Infeed Power / Bus Terminal Block:**
    - **Function:** Serves as the primary power and signal entry point for external 8V DC power and system common grounding.
### Power Architecture & Voltage Domains
The board operates on a strict **split-power architecture** sharing a common negative reference:
1. **Logic Domain (3.2V DC):**
    - Delivered directly from the CSB1 host controller via the 4-pin Qwiic cable (Red = 3.3V, Black = Logic GND).
    - Powers solely the internal logic of the two MCP23017 chips.
    - _Note:_ The breakout header `VCC` pins on the MCP boards remain disconnected to the DRV8833s.
 2. **Motor Domain (8V DC):**
    - Supplied by an external 8V DC layout accessory power supply landing on the infeed terminal block.
	    - This is supplied by a separate AC adapter, though could be the 12V accessory bus with a step down buck board set to 8V. The DRV8833 boards act unreliably with more than 10.8V.
    - Carries the continuous stall current for all 10 connected switch machines.
 3. **Common Ground:**
    - The external 8V power supply negative ($-$), the DRV8833 ground bus, and the CSB1/MCP logic ground line are tied together at the infeed block to establish a stable zero-volt reference across the logic-to-driver interface.
### Wiring Rundown
- **8V Power Spine:**
	- Power coming from the terminal block is routed to a 2x12 distribution module (A and B). 
    - Black ($+$) and White ($-$) Dupont connector wires are used for 8V to all DRV8833 `VM` and `GND` pins.
- **DCC-EX CSB1 Qwiic Connection:**
	- The CSB1 uses a 4-pin connector for the Qwiic output data. These 4 cables are routed to the corresponding ports in the MCP cable (not using `INTA` and `INTB`).
- **Logic Jumpers (MCP to DRV8833):**
    - 4-inch flexible Dupont ribbon jumpers running from the MCP output headers to the DRV8833 logic inputs (`IN1`–`IN4`).
    - Arranged in vertical stress-relief loops to prevent tension on header solder joints beneath the planned acrylic protective roof.
- **Motor Output Feeds (DRV8833 to Terminal Strips):**
    - Direct Dupont ribbon jumpers running from DRV8833 `OUT` pins directly into the screw-down terminal blocks at the edge of the board.
- **I2C Inter-Board Link:**
    - Connects Board 1 to Board 2 via daisy-chained Qwiic cable carrying `3.3V`, `GND`, `SDA`, `SCL`, `INTA`, and `INTB`).