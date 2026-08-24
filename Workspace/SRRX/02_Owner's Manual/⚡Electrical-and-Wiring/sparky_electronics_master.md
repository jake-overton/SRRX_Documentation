# SRRX ELECTRICAL & DCC POWER BLUEPRINT
# Authority: Sparky Electronics and Electric

## 1. DCC PRIMARY BUS SPECIFICATIONS
* **Main Bus Wire:** 14 AWG stranded copper wire.
* **Noise Elimination Protocol:** Primary bus wires must be strictly twisted at a rate of 10 to 12 turns per linear foot to eliminate inductive DCC signal distortion and digital cross-talk.
* **Feeder Wires:** 22 AWG solid copper wire. Maximum drop length from rail base to connection block is restricted to 6–12 inches to minimize voltage drop.

## 2. POWER ARCHITECTURE & DISTRIBUTION NODES
* **Zone Isolation Taps:** The main 14 AWG twisted bus is tapped using heavy-duty T-tap connectors to branch off dedicated sub-buses for individual electrical power zones.
* **Short-Circuit Protection Scheme:** Every localized zone sub-bus routes directly through an inline 1156 automotive tail-light bulb terminal block assembly. The bulb filament acts as a passive, visual current limiter to protect the main DCC booster and isolate shorts to a single zone.
* **Track Delivery:** Downstream from the 1156 short-protection block, the sub-bus feeds localized terminal blocks. These terminal blocks serve as the common distribution nodes for the individual 22 AWG track feeders soldered to the rails.

## 3. COMPONENT INVENTORY
* **Turnout Actuators:** 13 Circuitron Tortoise slow-motion switch machines in hand.
* **Tortoise Drive Current:** DC current supplied via dedicated accessory buses (separate from the DCC track bus).