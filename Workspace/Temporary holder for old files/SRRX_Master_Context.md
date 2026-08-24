# SILVER RIDGE RAILWAY (SRRX) — MASTER CANON ARCHIVE & SYSTEM CONTEXT
*Authoritative Reference for Project Decisions, Constraints, and Canon — Current as of August 2026*

---

## 1. Project Overview & Identity

* **Owner / Builder:** Jake Overton (Jonathan Daniel Overton)
* **Road Name:** Silver Ridge Railway
* **Reporting Mark:** SRRX
* **Scale:** N (1:160)
* **Era:** 1970s–2000s diesel era
* **Setting:** Rocky Mountain region (high alpine passes, steep cliffs, deep canyons, river gorges)
* **Character:** Practical shortline, grounded in historical operations (not tourist railroad tone)
* **Track Plan:** V10 (AnyRail) — current working plan; benchwork locked
* **Interchange Partner:** Denver & Rio Grande Western (D&RGW) — original and current Class I partner since SRRX founding in 1904 (D&RGW founded 1870). Historically grounded.

---

## 2. Layout Geography & Track Topology
[[Layout Electrical & Wiring Master Log]]

The layout features two mainline routes and specific district zones:
* **River Subdivision (River Run):** One mainline route.
* **Gorge Subdivision (Scenic Run):** The other mainline route.
* **Geographic Features & Districts:**
  * **Pine Valley Junction (PVJ):** North end, main staging and classification yard.
  * **PVJ Industrial Spur:** South side of PVJ (light blue on plan); serves warehouse and passenger depot; branches independently from mainline with **no connection** to the yard ladder; two tracks (Spur A and Spur B).
  * **Team Track / RIP Spur:** Gray track at the south end of the yard ladder; passive/multipurpose; absorbed into yard protection zone.
  * **Silver Ridge:** South end town and terminus.
  * **Silver Ridge Mine:** Northeast corner, upper right of plan.
  * **Moose Lake:** Near the mine, upper right of plan.
  * **Mine Branch:** Grade-intensive spur with switchback grades, ascending to the mine.
  * **Helper Pocket:** Staging for helper engines on mine ascents; part of PVJ yard protection zone.
  * **Silver Ridge Mountain:** The mountain mass in the northeast, featuring two tunnel bores on the north leg.
  * **Elk River Gorge:** East leg, south of the mountain (Confirmed canon name).
  * **Elk River National Park District:** National park area (Confirmed canon name).
  * **Southern Tunnel Portals:** Boundary between north and south halves of the layout.
  * **Timberline Lumber:** Industry spur on the east leg near Mill Pond.
  * **Timberline Fuel Depot:** Industry spur, daily operational stop.
  * **Smelter Spur:** Industry spur on the north leg, consolidated into Zone 2 sub-bus.
* **Topological Rules:** 
  * **No return loops or reverse loops anywhere on the layout.**
  * **The Mine Spur Vertical Window:** Located along the North Leg loop. The track climbs sharply on custom risers. At its closest crossing point, the bottom of the elevated Mine Spur roadbed structure must maintain **2" of vertical clearance** above the rail height of the mainline.

---

## 3. Geometric & Substrate Infrastructure

The physical layout substrate is divided into structural zones determining clearance calculations:

| Layout Location | Insulation Foam Thickness | Plywood Subroadbed | Total Substrate Depth |
| --- | --- | --- | --- |
| **North Leg Stack** | 1" Pink Foam | 11/32" Plywood | **1-11/32"** |
| **East Leg Stack** | 2" Pink Foam | 11/32" Plywood | **2-11/32"** |

* **Benchwork & Substructure:** L-girder benchwork utilizing the cookie-cutter method. Leg assembly shifted 6" eastward from earlier plans.
* **The 2-Inch Exclusion Rule:** Sub-plywood obstructions include laminated 2x4 leg blocks (3.0" x 3.5") and 1x3 vertical keeper joists (2.75" deep) running flush against the underside of the subroadbed. Any wire path, switch machine placement, or structural cutout within a **2-inch radius** of a framing barrier or introducing a vertical stack conflict must **FREEZE** until physical clearance is verified or overridden.

---

## 4. Electrical Architecture & Short Circuit Protection (`Sparky`)

* **Primary DCC Power Source:** CSB1 command station at 5A. No second booster installed or planned.
* **CSB1 Output Protection:** 5A inline automotive blade fuses on all four CSB1 output leads (`-a`, `+a`, `-b`, `+b`) via inline holders. Protects hardware, highly recommended by DCC-EX for DC-PWM operation.
* **Zone Short Circuit Protection (#1003 Bulbs):**
  * Short circuit protection across all **8 zones** (including Zone 1 / PVJ Yard) is provided by **CEC Industries #1003 automotive tail-light bulbs** wired in series on the hot rail (Rail A) only. Rail B passes straight through via jumper loop on barrier terminal blocks.
  * *Bulb Specs:* 12.8V, 12.032W, BA15s base, B-6 shape. Current ceiling when fully heated: ~0.94A (ideal for N-scale decoder protection, clamping just below typical N-scale stall currents of ~1.0–1.25A).
  * Self-resetting with visual fault identification (bulb illuminates during a short).
  * *Emergency Fallback:* Dual 1156-in-series is an approved backup *only* if 1003 stock is depleted at a zone. Single 1156 is prohibited.
* **Protection Zone Map (8 Zones):**
  1. **PVJ Yard:** Full yard ladder including helper pocket (Team Track/RIP absorbed).
  2. **Mine Spur:** Mine branch including switchback grades (Smelter spur consolidated here).
  3. **North Mainline:** PVJ throat through tunnel bores (boundary at southern portal).
  4. **PVJ Industrial Spur:** Warehouse and depot spur (branches independently).
  6. **South Mainline:** South of tunnel portals through gorge to Silver Ridge.
  7. **Timberline Lumber:** Timberline Lumber industry spur.
  8. **Fuel Depot:** Timberline Fuel Depot.
  9. **Silver Ridge Siding:** Siding at Silver Ridge terminus.
  *(Note: Zone 5 eliminated; numbering retained).*
* **Audible Fault Annunciator System (DEFERRED):** Designed using 8 × LM393 LDR sensor modules, a relay module, and a Walfront 12VDC piezo buzzer powered by the accessory bus. Components on Amazon wishlist; implementation deferred.
* **Wiring Specs & Busses:**
  * **DCC Main Bus & Sub-Buses:** 14 AWG red/black parallel zip wire. Main bus length: ~146.8 inches.
  * **Accessory Bus:** 14 AWG silicone wire (yellow and brown), 12VDC, 3A, stepped down via buck boards. Uses yellow T-taps for 14 AWG and ferrules for 24 AWG branch connections.
  * **Track Feeders:** 22 AWG solid-core wire (white and blue), dropped directly to rail base (max length 6–12 inches where possible).
* **Accessory Automation:** 13 Circuitron Tortoise slow-motion switch machines driven by a dedicated, completely isolated DC accessory power bus.

---

## 5. Trackwork & Turnout Matrix (`Lieutenant Layout`)

* **Track Standards:** Atlas sectional and flex track for mainline, sidings, and industrial spurs.
* **Turnouts:** Atlas N-scale on mainline; Peco N-scale turnouts exclusively for classification yard ladder throat (20 total Peco turnouts in hand).
* **Roadbed:** 1/8" Atlas cork roadbed on mainline. Sub-yard tracks and ladder throat laid flat on pink foam.
* **Turnout #3 Choke Point Resolution:** Resolved by moving leg assembly eastward to clear the yard ladder.
* **Track Laying Procedure:** Clear acrylic latex caulk (with silicone) is the standard adhesive. Sequence: Tack → Hand-test rolling stock → Mark holes → Remove track → Solder feeders to track while on the bench → Drill & vacuum → Apply caulk → Drop feeders & seat track → Cure → Solder remaining feeders → Connect feeders to terminal bus.

---

## 6. Landscape, 3D Fabrication, & Finishes (`Professor Paint & Sally Scenery`)

### **3D Fabrication Standards:** 
Lineside structures, figures, and kits custom-printed in PLA and resin. PLA must be sanded, coated with fill-primer to eliminate layer lines, and sealed before painting.
### **Visual Concealment Protocol:** 
All visible trackage should receive weathered grimy black/rust rail profiles. Mechanical linkages, torsion sleeves, and actuator wires painted flat grimy black or masked with scenery.
### **Key Structures & Scenery Inventory:**
  * **Silver Ridge Town:** 
    - **Bank** — H_Pendergast 3D print — painted complete — baking soda stucco technique on upper floor, two-tone, corner entrance with balustrade
    - **Elk River Outfitters** (formerly Shop #1) — H_Pendergast 3D print — painted complete — orange brick, white trim, green awnings
    - **Pergandes Brewery** — Blair Line kit — completed April 2025 — painted complete — local craft brewery, recreational not operational; no freight customer status; name from kit facade, no personal significance
    - **Three Sears houses** — unpainted gray — painting and interior LED lighting are next project
    - **Red bungalow** — painted complete — private mountain retreat; possible residence for federal building director (rented); tentative placement near river bend — may not make final layout
    - **Federal building** — 3D printed — painted complete — red brick, Palantir logo over door (Easter egg for younger son), cocktail umbrella communications dish, razor wire chain link fence, on hill outside Silver Ridge — cover name TBD; black Suburbans (white PLA, to be painted black with tinted windows) for parking lot

  * Gorge Flagstop
    - **Overton Coach depot** — Blair Line kit — painted complete — dark brown wood, covered Victorian porch, foil roof weathering, micro LED in porch ceiling (wires not yet run)
    - **Gorge-ous Grub** — converted ATSF caboose #2 — conversion pending
    - **Resin picnic tables** — in hand — placeholder umbrellas until suitable N scale set sourced
    - **NPS welcome sign** — to be laser cut, NPS colors (brown post/border ~Pantone 476)

  * Wildlife and Figures
    - Elk (family), moose, bears — mini-prints resin — placement near Moose Lake, park district, mountain/gorge
    - 100 painted people figures — various poses
    - Gas station with pumps, barrels, tires — Silver Ridge
    - Two 1960s Suburbans (white PLA) — to be painted black, tinted windows — federal building parking lot

### Baking Soda Technique
Baking soda mixed into paint creates stucco texture. Document ratio used on Bank for future structure consistency.

---

## 7. Gorge Flagstop — Canon Summary

- **No formal name** — milepost designation only
- **Conditional summer stop** on Valley Flyer; bypassed in winter except ad hoc
- Gateway to Elk River National Park District
- Structures: Overton Coach depot + Gorge-ous Grub caboose + picnic area
- NPS welcome sign across tracks names the park, not the stop
- Local informal reference: "the gorge stop"

---

## 8. Personal Connections (from Foreword)

- **Burlington Route freight car** — Uncle Dick (Richard Carlton Overton) wrote *The Burlington Route*
- **Dew Drop Inn** — named for bar Jake's father (Dick) frequented after NY Giants games, Weehawken NJ, ~1970s
- **Silver Ridge inspired by Steamboat Springs, CO** — oldest son lives there with wife and grandson; son is CFO of Yampa Valley Bank
- **Federal building** — honors younger son who works at Palantir; logo is the Easter egg
- **Overton Coach depot** — coincidental Overton name connection; William Dayton Overton built the original cars in 1870s-80s
- **Jake's last name: Overton**

---

## 9. Operational Parameters & Fleet Lore

* **Operating Philosophy:** Continuous, free-flowing mainline running paired with localized industrial switching guided by historical narrative.
* **Primary Passenger Consist (*The Valley Flyer*):** Pulled by EMD GP7/GP9 Locomotive **SRRX 102** (deep maroon livery with silver-white striping). Observation car #2780 has a **permanent non-coupled rear**, always facing the PVJ end.
* **Seasonal Directives:**
  1. *Summer Tourist Mode:* Departs Silver Ridge Depot, traverses outer alpine loop, terminates at PVJ depot/yard.
  2. *Winter Transit Mode:* High outer loop snow-blocked; consist restricted to inner gorge run and inner tunnel as a winter commuter/mail lifeline.
* **DC/DCC Operation:** CSB1 supports both DCC and DC PWM via TrackManager (default 131Hz PWM on ESP32). Initial track testing utilizes DC locomotives before fleet conversion. Proper TrackManager mode configuration is required prior to placing DC power on rails.

### Definitive Roster
* **Switchers:**
  * No. 98 — GE 70-Ton — L&N livery — black — DCC operational (Address 98) — primary yard switcher & mine helper.
  * No. 101 — GE 44-Ton — red — DCC installed — stalls forward — axle swap pending.
  *(Note: There is no 40-Ton GE; removed as a data entry error).*
* **Road Locomotives:** SP #5017 (GP-30, Atlas, DC candidate); MoPac #4637 (GE B23-7, Bachmann, DC candidate).
* **Passenger Power:** ATSF F9A #215 & F9B #215 (Dummy) — Valley Flyer power.
* **Passenger Equipment:** Obs #2780 (permanent rear coupler); Coach #1919.
* **Cabooses (3):** ATSF caboose #1; ATSF caboose #2 (faded pink cupola, slated for Gorge-ous Grub conversion); PRR caboose.
* **Freight Fleet:** Assorted ore hoppers, tank cars (Shell, Dow, Hooker, Penn Salt), boxcars, and EL #95909 Russell Snow Plow (MOW at PVJ).

---

## 10. Administrative & Workflow Notes

* **Google Drive Folder:** `SRRX Operations Manager` (`/Documents/`, `/Data/`, `/Fleet Photos/`).
* **App State:** `SRRX_Operations_v3.html` is the active single-file HTML operations manager.
* **Output Format:** Markdown with Affinity Publisher style tags when generating handbook or document content.
* **Core Rule:** One-variable-at-a-time troubleshooting; all numerical calculations must be run through executable code.