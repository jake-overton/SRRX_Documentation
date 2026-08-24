# MASTER CONTEXT: SILVER RIDGE RAILWAY (SRRX)
*Last Updated: 2026-06-08 | Scale: N (1:160) | Era: 1970s-2000s Diesel | Setting: Rocky Mountains*
*Philosophy: Practical shortline, not a tourist road. One railroad, one cohesive geologic story.*

## 1. PROJECT METADATA & GEOGRAPHY
* **Founded:** 1904. **Interchange Partner:** Denver & Rio Grande Western (D&RGW) since founding. Do not alter/confuse.
* **Core Nomenclature:** PVJ = Pine Valley Junction (Never "Port Vance"). 
* **Valleys & Hydrology:** Broader region is the Elk River Valley, bridging two distinct drainages across a mountain divide.
  * *Pine River:* Cuts east-west across North Leg. Carved down into 1" foam below operational zero datum.
  * *Elk River:* Flows south through valley (+2" elevation), hits an E-W fault line, turns hard west into a steep, straight-walled, vertical-face canyon (The Gorge). Floor drops from -0.5" to -2.5" at exit. Replaces "Silver Ridge River" everywhere.
* **Unifying Fault System:** An E-W regional fault controls the river's turn into the Gorge, creates vertical canyon walls, and dictates the Silver Ridge Mine's location on the NW face (exploiting a mineralized contact zone between metamorphic basement and intruded igneous body).

## 2. TRACK PLAN & CONSTRUCTION (V10 ANYRAIL)
* **V10 Relocation Note:** Smelter moved from East Leg to a teal stub-spur on the Mine Branch (North Leg) before the first switchback. Eliminates implausible cross-mountain ore transit. Mainline inner tunnel adjusted; first switchback tail lengthened.
* **Benchwork & Foam:** L-girder framework mobile on casters complete (operator-side open for underside wiring access). Plywood top laid loose. 1:1 scale V9 template laid out for geometry.
  * *North Leg:* 1" pink foam base (Operational Zero Datum).
  * *East Leg:* 3" total foam stack (1"+2" sheets stacked) to hold a steady +2" elevation above the yard.
  * *Foam Stock:* 1x (4x8'x2") and 1x (4x8'x1") in hand. **CRITICAL NEED:** Source one additional 1" foam sheet to begin cutting.
* **Mountain Contours:** Stacked foam layers carved to organic shapes using V10 contours as cutting templates, sheeted with Sculptamold. Strata transitions from horizontal, slightly tilted sedimentary layers (limestone/shale) lower down, to sharp, jointed metamorphic rock (gneiss/schist) on the upper mine shelf and cirque headwall.

## 3. DCC INFRASTRUCTURE & WIRING GRID
* **Control System:** NCE Pro Cab / Cab06 Wireless. Command Station is a single **CSB1 at 5A**. No boosters.
* **Short Circuit Strategy:** Localized passive current limiting via **GE 1156 automotive tail light bulbs** wired in series with the Rail A bus feed for each isolated section. Held in nylon wire clamps under benchwork. *RULE: NCE EB1 electronic breakers are completely benched. Do not suggest them or boosters.*
* **Bus Spec:** 14 AWG solid copper main bus (Red=Rail A, Black=Rail B) under L-girders. 22 AWG stranded feeders (max 12" runs), tapped via IDC suitcase connectors and soldered to outer rail bases.
* **9 Power Districts (Isolation Zones):**
  * *z1 (North Mainline):* PVJ throat through tunnel bores to southern portals.
  * *z2 (South Mainline):* South of tunnel portals through the Gorge to Silver Ridge town.
  * *z3 (PVJ Yard):* Full classification ladder, helper pocket siding, and absorbed Team Track/RIP line.
  * *z4 (PVJ Industrial Spur):* South side independent warehouse/passenger depot branch. No yard connection.
  * *z5 (Mine Spur):* Mine branch line including all 3-stage switchback tails. Grade-heavy, wheel-slip risk.
  * *z6 (Timberline Lumber Spur):* Industrial lumber reload track on East Leg (+2.5" elevation).
  * *z7 (Smelter Spur):* Dedicated industrial track for newly relocated silver smelter on Mine Branch.
  * *z8 (Fuel Depot Spur):* Timberline Fuel Depot tank car drop point inside National Park boundary.
  * *z9 (Silver Ridge Siding):* Passing/runaround siding at Silver Ridge town terminus.
* **Wiring Schematic Update:** Need to update the Affinity Designer layout file (DXF base) to strip EB1/booster symbols and add 1156 bulb symbols across the 9 zones.

## 4. FLEET ROSTER & COUPLER CONSTRAINTS
* **Switchers:** * *No. 98 (GE 70-Ton, Black L&N):* DCC Operational (Address 98). Primary yard goat and switchback helper.
  * *No. 101 (GE 44-Ton, Red):* DCC installed. Stalls moving forward (suspected bent axle). *Diagnostic Backlog: Axle swap using parts from No. 98 is pending.*
  * *ROSTER DEFENSE:** There is NO 40-Ton GE. Correct this data entry error to 44-Ton globally in manual/app.
* **Road & Passenger Power (DC Candidates / DCC Conversions Pending):**
  * *SP #5017 (Atlas GP-30):* Verified GP-30 after underframe inspection (previously labeled SD40). Primary road engine.
  * *MoPac #4637 (Bachmann GE B23-7):* Interchange representative engine.
  * *ATSF #215 (Bachmann EMD F9A) & F9B Dummy:* Valley Flyer passenger power. High "white gear" split risk; no decoder space found. *RULE: Do not invest in custom decals/paint for this train until DCC/mechanical issues are solved.*
* **Passenger Consist & Fixed Orientation Rule:**
  * *Consist:* F9A + F9B + Coach 1919 (plastic wheels, replacement pending) + Observation 2780.
  * *ABSOLUTE RULE:* **Obs2780 permanently lacks a rear coupler.** Therefore, it must always sit on the PVJ end of the Valley Flyer, and the F9A must pull from the Silver Ridge end. Operates as a fixed push-pull shape that cannot be reversed.
* **Freight Car Allocations:**
  * *The Mine Run:* BN #95913, Thunder Bay #798, PRR #262581, B&O #21022 (Heavy ore hoppers). *P&LE #43221 open hopper with coal load is a candidate for ore conversion.*
  * *The Smelter/Hazmat Run:* Shell #1245, Dow #14003, Hooker #69502, PennSalt #67927 tank cars.
  * *Interchange/Lumber:* MTL Gondola (only freight car with Micro-Trains truck knuckles installed), Burlington #85117 hopper, Swift #4244 reefer, LV #41033 boxcar.
  * *MOW:* EL #95909 Russell Snow Plow stored at PVJ.
* **Cabooses:** ATSF 1 and PRR are operational candidates. ATSF 2 has a broken smoke stack and faded pink cupola (salvaged weights); benched for scenic conversion into the Gorge-ous Grub stand.
* **Coupler Project:** Standardizing the mixed fleet to MT knuckles is an active backlog item.

## 5. PAINTS, FINISHES, & VECTOR DECAL LAYOUT
* **Structure Paint Asset:** Rattle can Rust-Oleum Matte Hammered Black (Date Code 012808). Repurposed 20-year-old stock. Hammered texture perfectly mimics aged asphalt shingles or industrial tar paper at 1:160 without needing weathering powder.
* **Airbrush Protocol (Gocheer Entry-Level Kit):** 0.3mm nozzle experienced a severe metallic pigment clog from silver fence paint on 2026-06-07 (currently soaking overnight in cleaner). 
  * *CRITICAL COMPLIANCE RULES:* Never spray metallic paint through the 0.3mm nozzle again. Use the 0.5mm nozzle for all metallics and large body coats (e.g., the upcoming caboose body). Use airbrush medium, never water, to thin metallics. Never stop flow mid-session without an immediate flush.
* **Decal Strategy:** Custom artwork generated in Affinity Designer using hex values from Handbook Appendix D. Will be exported to vector PDF/AI and sent to a commercial printer (Circus City, Herald King, etc.) to achieve opaque white/cream lettering over dark backgrounds. Cars must be manually caliper-measured in millimeters first.
  * *Priority 1:* Gorge-ous Grub caboose (SRRX Maroon/Cream with custom restaurant branding). Cupola painted brick red before brush clog; body pending.
  * *Priority 2:* Valley Flyer benched indefinitely until mechanical gear/DCC questions are settled.

## 6. STRUCTURE KITS & LANDSCAPE INVENTORY
* **Sears Catalog Residential Block (Silver Ridge):** Three kits in hand (Rodessa, Lorain, Purita) with separate roofs. Primary targets for airbrush training progression after nozzle recalibration.
* **Gorge Flagstop Depot:** N Scale Architects #10051 Overton Coach Flag Stop Station in hand (includes attached privy). Sits in Gorge country along with 3D-printed Gorge-ous Grub outdoor picnic/umbrella tables.
* **The Dew Drop Inn:** Acquired Blair Line kit (originally named 'Green Door Lounge'). This is a permanent anchor for Silver Ridge town. *Note: Ordered a duplicate copy by mistake. Keeping both. Copy 1 = Silver Ridge Dew Drop Inn. Copy 2 = PVJ pub/diner (Name TBD). Will differentiate via entirely unique siding/trim colors, signage, and placement on opposite ends of the mountain.*
* **Silver Ridge Passenger Depot:** Blair Line Blairstown 2-story kit in hand. Footprint must be checked against Silver Ridge town loop geometry before benchwork is permanently locked.
* **Federal Building Block:** Perched on the hill above town. Painted brick red on June 7 (PLA texture acceptable as rough masonry). Pending: concrete gray horizontal accent bands and dark charcoal/olive window shades. Ground space accommodates an edge-to-edge parking lot with 1-2 period-correct 1980s government Chevy Suburbans and a 3D-printed tactical satellite dish (1.5" to 1.9" N scale diameter for a 20-25ft military dish array).
* **NPS Entry Sign (Gorge Boundary):** 3D model evaluating stage (~25mm wide at N scale). Features trees, mountain, and NPS arrowhead. Plan: Resin print + basswood posts + foam/Sculptamold stone base + custom typography decal (Twentieth Century Condensed ~5.7pt at 75% horizontal scale). No taglines.
* **H_Pendergast 3D Print Collection (Thingiverse):** "Turn of the Century Town" complete set acquired. Includes 9 shops, blacksmith, sheriff, two banks, school, general store, city hall, and fire station. Consistent scale and cohesive aesthetic. Blacksmith fits Silver Ridge character perfectly; school and fire station marked for upcoming makerspace test prints. Excessive buildings will serve as overflow structures to populate Pine Valley Junction.
* **Industrial Scenery Anchor:** Slag pile planned on the down-slope side of the V10 Smelter, cascading toward the Gorge. Geologically realistic; predates the National Park boundary to establish intentional visual/political narrative tension.

## 7. HANDBOOK STATUS & OPERATIONAL BACKLOG
* **Software:** Affinity Publisher. Main text format is written in Markdown embedded with explicit AP paragraph and character style tags for direct find-and-replace compilation. 
* **Current Edition:** v1.1 PDF in workspace. Sections Foreword through AppF are complete, but require immediate global editing sweeps to clean up V10 changes.
* **Foreword Narrative Anchors:**
  * *Richard Carlton Overton:* Great uncle, Burlington Route historian; tied to car Burlington85117.
  * *Dick Overton:* Father, NY Giants fan, Weehawken NJ waterfront bar; tied to Dew Drop Inn.
  * *Cole & Grandson (Born Feb 2025):* Son lives in Steamboat Springs CO, works at Yampa Valley Bank; tied to Elk River Valley Bank name.
  * *Charlie:* Son, Palantir NYC software engineer; tied to the high-security Federal Building block.
  * *William Dayton Overton:* 1870s carriage/coach builder; coincidental family name tied to the Overton Coach depot and Flyer passenger cars.
* **IMMEDIATE HANDBOOK EDITORIAL TASKS:**
  1. Global find-and-replace: Change **40-Ton GE** to **44-Ton** everywhere (including Appendix F).
  2. Global find-and-replace: Change **Silver Ridge River** to **Elk River** across all text blocks.
  3. Apply `SRRX_Handbook_Updates_Draft.md` (Gorge flagstop, NPS sign, Silver Ridge inventory, Flyer fixes).
  4. Layer `SRRX_Handbook_Updates_V10.md` on top (The heavy structural shifts for the Smelter move).
* **OPEN UNRESOLVED LOGISTICAL RIDDLES:**
  * *The Chemical Tank Car Routing (Hooker, Dow, Penn Salt):* In V9, they were spotted via the Scenic Run Local. In V10, the Smelter is on a steep, stub-ended branch spur off the Mine Branch with zero runaround room at elevation. We must design a new movement protocol: either update **Section 8.1 (The Mine Run)** so the heavy ore train drags/drops them on its way up, or create a brand-new **Section 8.x (The Smelter Local)** where a dedicated switcher pushes the tank cars up the hill. 
  * *Section 8.4 Update:* Retitle strictly to "Timberline Fuel Depot" and wipe all historical Smelter references.
  * *The Silver Ridge Hotel Ghost:* Section 8.7 mentions a town hotel that does not exist in the structure inventory. Must decide to add a building to the track plan or strip it from the text copy.
* **Owner's Manual Project:** Separate builder's technical log. Section 1 (`SRRX_OwnerManual_Wiring_v1.md`) detailing the 1156 short-circuit philosophy is drafted and ready for local download/Drive sync. Next step: Develop the master overview and layout benchwork outlines.