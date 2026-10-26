Burying the board roadside and bending the optical leads $90^\circ$ solves several mechanical headaches: you bypass drilling through the cork/XPS/plywood stack, clear the Tortoise throw mechanisms below deck, and keep the calibration trim pots accessible from the surface.

  

To make roadside diffuse-reflective sensing reliable in N scale, account for the following geometry, optical shielding, and scenic integration factors.

  

### 1. Optical Angle and Elevation Geometry

When firing across the track rather than up from the ties, two physical failure modes occur if the sensors fire straight horizontal: **inter-car gap dropouts** and **reflection bounce-off on curved car sides** (like cylindrical hoppers or tank cars).

  

- **Beam Height (Z-Axis):**
    
      
    - Target **10 mm to 12 mm above the railhead**.
        
          
        
    - At this height, the beam hits the solid vertical side sheets of standard boxcars, reefers, locomotives, and cabooses.
        
          
        
    - _The Flatcar / Skeleton Car Trap:_ A beam at 10 mm will shoot straight over an empty flatcar deck or bulkheads. If your fleet includes empty flats, drop the beam centerline to **5 mm to 6 mm above railhead**. This targets wheel trucks, side sills, and bolster frames directly without clipping rail tops.
        
          
        
- **Beam Angle (Cross-Track Angle):**
    
      
    - **Do not fire at a 90° right angle to the rail.** A perpendicular beam passes cleanly between car gaps, producing severe toggle chatter on the digital line.
        
          
        
    - Angle the emitter and receiver **$30^\circ$ to $45^\circ$ diagonally across the track** relative to the direction of travel.
        
          
        
    - A diagonal path lengthens the target footprint, allowing the beam to catch the leading and trailing ends of cars before the car body leaves the detection zone, bridging the gap between couplers.
        
          
        

### 2. Lead Bending and Optical Isolation

Because these LM393 modules rely on diffuse reflection, cross-talk between the onboard emitter and phototransistor will blind the sensor if they are not isolated:

  

- **Bending the Leads:**
    
      
    - When bending the 3 mm / 5 mm LED leads $90^\circ$, **support the base of the lead with smooth needle-nose pliers** between the diode epoxy body and the bend point. Bending the wire directly against the resin lens can fracture the internal bond wires or crack the casing.
        
          
        
- **Optical Crosstalk Collar:**
    
      
    - When bent horizontally side-by-side, the emitter’s peripheral scatter can bleed directly into the phototransistor lens without ever bouncing off a train.
        
          
        
    - Slip a short collar of **matte-black heat-shrink tubing (4 mm to 6 mm long)** over the phototransistor, extending roughly 1 mm to 2 mm past the tip of the clear bulb to act as an optical "lens hood" / snoot.
        
          
        
    - Keep the emitter and receiver physical axes angled slightly inward (toed-in by $5^\circ$ to $8^\circ$) so their focal points intersect right over the track centerline.
        
          
        

### 3. Scenic Disguise Strategies

Because the board requires top-side access to adjust the potentiometer when room lighting shifts or paint finishes change, do not glue scenic material directly to the PCB.

  

#### A. The "Removable Shell" Technique

- **Lineside Trackside Cabinets / Relay Sheds:**
    
      
    - A small styrene or 3D-printed lineside relay cabinet (or battery box / tool shed) makes an ideal hollow slip-cover.
        
          
        
    - Drill two micro-holes (1/8″) in the side wall facing the track for the optical lenses.
        
          
        
    - Drop the structure over the vertical or flush-mounted board. When calibration is needed, simply lift the shed off the ground to reveal the trim pot.
        
          
        
- **Culverts, Drainage Ditches, and Concrete Retaining Walls:**
    
      
    - Mount the board flat inside a shallow recess cut into the top layer of the XPS foam just outside the ballast shoulder.
        
          
        
    - Paint the exposed board face flat earth/camo drab (keep the pot wiper clean).
        
          
        
    - Run the optical leads through two small corrugated styrene pipes embedded into a scenic embankment or drainage culvert wing wall facing the rail.
        
          
        
- **Lineside Vegetation / Shrub Clusters:**
    
      
    - Mount the board inside an XPS foam trench.
        
          
        
    - Adhere a cluster of lichen, coarse turf, or a clump-foliage canopy onto a small base of thin styrene or cardstock.
        
          
        
    - Place this "foliage plug" directly over the potentiometer cavity like an access hatch.
        
          
        

### 4. Calibration for Weathered Rolling Stock

Side-reflection detection is sensitive to surface sheen: factory gloss plastic bounces infrared cleanly, while weathered, chalky, matte-finish cars (especially dark brown boxcars or black tank cars) absorb IR.

  

1. **Test with the Worst-Case Car:** Place your most heavily weathered, matte-black or dark-oxide car on the track directly in front of the angled sensor.
    
      
    
2. **Dial the Potentiometer:**
    
      
    - Turn the trim pot until the onboard output indicator LED lights up solid (digital LOW).
        
          
        
    - Back it off just slightly past the flicker point to avoid ambient room light triggering it when the track is clear.
        
          
        
3. **Verify Ambient Rejection:** Remove the train and turn on all office/room lighting. Ensure the indicator turns off completely and does not chatter.
    
      
    
4. **Software Timing:** Retain a software off-delay (minimum **800 ms to 1000 ms**) in your Arduino script to ensure that even if an inter-car coupler gap briefly drops the reflection, the block status remains latched `OCCUPIED` until the train has fully cleared the zone.