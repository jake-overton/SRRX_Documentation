### 1. Optical Geometry & Track Integration (N-Scale Code 80)
Because N-scale rolling stock underbodies vary widely (smooth plastic tank cars vs. ribbed boxcar floors vs. open-frame flatbeds), positioning and physical geometry determine optical reliability:
-  **Mounting Style (Under-Track Upward Reflective):**
	- Mount the IR emitter/phototransistor pairs firing **vertically upward** between the ties.
	- In Atlas Code 80 flex track, remove or shave down the small plastic webbing between two adjacent ties rather than cutting the rail ties themselves.
	- The sensor face should sit flush or recessed approximately **0.5 mm to 1.0 mm below the top edge of the ties** (roughly 1.5–2.0 mm below railhead). Never let the emitter/photodiode package sit proud of the tie plane to prevent snagging low-hanging locomotive cowcatchers, trip pins, or coupler air hoses.
- **Axial Offset (The Centerline Trap):**
    - Do not align the sensor dead-center between the rails if running flatcars or empty skeleton log/skeleton spine cars.
    - Offset the optical centerline **1.5 mm to 2.0 mm off-center** toward one rail. This guarantees that wheel flanges, truck bolsters, or axle hubs trip the reflection even across skeletal frames or narrow wheelbases.
- **Ambient Light Shielding:**
    - Unmodulated reflective sensors (LM393 comparator-based boards / TCRT5000 style) are vulnerable to overhead layout room lighting (especially fluorescents or changing sunlight).
    - Use a small length of matte-black heat-shrink tubing (approx. 2 mm inside diameter) around the phototransistor, or sleeve the subroadbed hole with a brass/styrene tube painted ultra-flat black inside. This restricts the photodetector’s field of view strictly upward toward the passing train, blocking off-axis room light.
### 2. Layout Placement Strategy (SRRX Subroadbed & Trackwork)
On your 11/32″ plywood and XPS foam subroadbed with cork roadbed, placement should follow a deterministic boundary-pair architecture:
```
[Entry Sensor A] ------------ Block Interior (Hold Latch) ------------ [Exit Sensor B]
   (Clearance)                                                            (Fouling Pt)
```
#### A. Turnout Clearance & Fouling Margins
- Never place a detection sensor directly inside the turnout closure rails or frog.
- **Turnout Approach:** Place the boundary sensor at least **2.5 inches (65 mm)** back from the point of switch. In N scale, this gives your DCC-EX automation enough lead time to verify turnout alignment or cut track power before a train runs through against the points.
   - **Turnout Frog/Fouling Point:** Place the trailing fouling-point sensor at the exact spot where adjacent track centerlines diverge past **1.25 inches (32 mm)**. Any car stopping short of this point will sideswipe traffic on the converging route.
#### B. Siding & Passing Loop Architecture (Entry/Exit Boundary Pairs)
- Use two sensors per block:
    1. **Entry Detector:** Located at the entrance fouling point. Trips the block to `OCCUPIED`.
    2. **Stopping/Exit Detector:** Located at the far clearance point (leaving roughly 3 to 4 inches of stopping runout before the exit signal or turnout points).
- **Software Latching:** Since IR sensors detect point targets rather than continuous wheel current, rolling stock gaps (coupler pockets between 40-foot boxcars) will cause the digital line to bounce high/low. Latch the block `OCCUPIED` upon the first trigger of Sensor A, maintain occupancy through the gap bounce via software, and release to `CLEAR` only after Sensor B triggers and sees an unbroken beam-rest (or exit clearance) for a sustained window.
#### C. Concealed Tracks & Tunnels
- Tunnel portals and hidden staging tracks naturally shield ambient light, giving the highest reflective contrast.
   - Place one sensor **1.5 inches inside the portal entrance** and another **1.5 inches before the exit portal**.
### 3. Drilling, Subroadbed Prep & Mechanical Integrity
Drilling through the multi-layer deck (cork + XPS foam + 11/32″ plywood) requires clean vertical alignment to prevent misaiming the optical beam:
1. **Pilot Hole from the Top:**
    - Mark the exact tie pocket. With track already pinned or caulked, use a hand pin vise or micro drill bit (approx. 1/16″ or #52) to drill straight down through the cork and into the foam between the ties.
2. **Clearance Bore from Below:**
    - From the underside of the benchwork, enlarge the hole through the 11/32″ plywood with a 5/16″ or 3/8″ spade bit, stopping just as it bites into the XPS foam.
    - Push a rigid plastic guide tube (e.g., Evergreen styrene tubing) upward through the foam to the bottom of the cork roadbed.
3. **Mounting the Board/Sensors:**
    - If using discrete 3mm/5mm IR LEDs/phototransistors desoldered and tethered to the LM393 boards, slide the sensor pair up into the styrene tube from underneath, locking them in place with a dab of removable tacky glue or a snug friction-fit collar.
    - If mounting the entire small breakout board beneath the deck, mount the board to a 3D-printed bracket screwed into the plywood underside, keeping the potentiometers accessible for bench calibration.
### 4. Calibration & Signal Conditioning
- **Threshold Potentiometer Adjustment:**
    - Place your darkest, least-reflective piece of rolling stock (e.g., weathered matte-black hopper or boxcar underbody) over the track hole.
    - Turn the onboard trim pot until the module output goes active (digital LOW on standard active-low LM393 modules).
    - Remove the car, check under full room lighting (with normal layout operating lights on), and confirm the sensor cleanly returns to inactive (digital HIGH). If overhead lights hold it active, increase the depth of the phototransistor shroud.
- **Debounce / Off-Delay Timing:**
    - In the Arduino / DCC-EX software layer, apply an **off-delay timer of at least 800 ms to 1200 ms**. At slow switching speeds (scale 5–10 mph), the open space between coupled trucks can take 0.5–0.8 seconds to traverse a single optical point; a 1-second timeout prevents false "block clear" chatter.