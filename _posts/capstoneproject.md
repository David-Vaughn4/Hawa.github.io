
---

# **Digital Portfolio – Oscillating Fan Project**

---

## **Research**

### **Description of final project choice, why chosen, and what a successful project would do**

For my final project, I chose to design and build an oscillating fan. I selected this project because it combines mechanical motion, electronics, and programming, allowing me to apply multiple skills learned during the course. An oscillating fan is also a practical, real-world object that demonstrates how motors, linkages, and control systems work together.

A successful project would safely produce airflow, rotate side-to-side in a controlled oscillating motion, and operate reliably for extended periods of time. The fan should be stable, reasonably quiet, and easy for a user to turn on and off. Ideally, the oscillation speed and fan speed could be adjusted.

---

### **Attribution of project serving as inspiration**

This project was inspired by several DIY oscillating fan and motor control projects found on **Instructables** and **Adafruit**. In particular, I referenced projects that used Arduino-controlled DC motors and servo motors to create oscillating motion.
Sources included:

* Instructables.com – DIY Arduino Fan Projects
* Adafruit Learning System – Motor and Servo Control Guides

These sources helped me understand motor wiring, PWM control, and safe power usage.

---

### **Description of how project is different than source**

Unlike the reference projects, my oscillating fan design uses a custom-designed fan housing and base, created specifically for this project. I also modified the oscillation mechanism to use a geared DC motor rather than a simple servo sweep, allowing smoother and more realistic fan motion. Additionally, I focused on creating a compact, stable design that could be fabricated using Fab Lab equipment instead of off-the-shelf enclosures.

---

### **Design Specification Considerations document**

I completed a Design Specification Considerations document that addressed:

* Safety (covered blades, stable base)
* Power requirements and voltage limits
* Material choices for durability and weight
* Size constraints
* Ease of assembly and maintenance

These considerations guided my design decisions and helped prevent issues during fabrication.
Name of Project: LED Fan
Tutorials:
https://www.instructables.com/Programmable-LED-Fan-A-Light-Breeze/ 
https://www.instructables.com/Ceiling-Fan-LED-Display/ 
https://www.youtube.com/watch?v=6TPGJ8Aejew 
3D Fan Design: A Step-by-Step Guide: #hycadtutorials
Fusion 360 Tutorial #83 | 3D Model Design Basic Beginners - FAN CPU
https://www.youtube.com/watch?v=C2wyVuTTmmM 




Jaden: Base
Materials: 
DC motor
straight/L/T shaped pvc pipes
Wood for base (either circular or cross shaped). 
Oscillating motor:
https://www.youtube.com/watch?v=EbjXVf9PgaE 
https://www.youtube.com/watch?v=oiRhuAQ1eHw 
Materials and parts needed for this project:
Geared TT motor (x1) - https://amzn.to/3IMl5Le
PWM speed controller (x1) - https://amzn.to/3Zx6RE1
On/Off Rocker switch (x1) - https://amzn.to/3IMdSuX
XT60 20V female connector (x1) - https://amzn.to/3X7nZP6
12V Barrel jack connector (x1) -  https://amzn.to/3CNOP6J
*20V laptop adapter (x1) - https://amzn.to/3XwFckH
12V Adapter (x1) (not required, best use buck converter module to achieve 12V) - https://amzn.to/3XbsiZF I THINK I HAVE ONE!
LM2596 DC-DC Buck converter module (x1) - https://amzn.to/3kd9pXN
Electrical wire 24AWG - https://amzn.to/3GGny7j
Cork (x1)
Bicycle spoke (x1) - https://amzn.to/3kgPDdQ
Skateboard bearing (x1) - https://amzn.to/3Wb8wfR
Washer (x1) - https://amzn.to/3J4vouD
Cheap pen (x1) - https://amzn.to/3GGnF2J
Popsicle sticks (x3) - https://amzn.to/3H3vMb5
3/4 inch PVC pipe - 4 inches tall (9cm)
Screws (x2)
14x14cm Square piece of wooded plank (x1)
Small hexnuts (x4)



Comparison: “Programmable LED Fan – A Light Breeze” vs “Ceiling Fan LED Display”
Aspect
Light Breeze
Ceiling Fan LED Display
Goal / approach
Add an LED strip to a fan blade, use a slip ring to send power/data while spinning, and control via Arduino/RPi. 
Instructables
Build a full persistence-of-vision (POV) display on a ceiling fan by mounting multiple LED boards on blades, with an Arduino-based control and synchronization. 
Instructables
Complexity
Relatively simple: one strip, minimal electronics, simple wiring
More complex: multiple LED boards, custom PCBs, synchronization, more wiring, more steps
Mechanical modification
Use a thrift-store fan, glue slip ring, mount LEDs, balance blades, run wires out front cover. 
Instructables
Cut/replace blades (e.g. plywood), mount custom LED boards on blades, route wiring toward center, use harnesses, hall effect sensor for timing. 
Instructables
Electronics / driving LEDs
Uses addressable LED strips (Neopixels, DotStar) soldered to slip ring wires. 
Instructables
Uses discrete LED boards with shift registers (74HC595), voltage regulators, microcontroller (ATmega / Arduino) per blade/board and central MCU, etc. 
Instructables
Synchronization / timing
You just send patterns; less demand for precise timing (unless syncing animations)
Uses a hall effect switch (magnet + sensor) to detect rotation once per revolution to trigger timing loops. 
Instructables
Pros / trade‑offs
Faster to build, lower cost, simpler
More flexibility (images, animations), more polished display, more custom work
Which to pick based on your goals
If you just want a spinning LED effect with minimal effort, Light Breeze is more achievable. If you want full POV images or more advanced display control, go for Ceiling Fan style (but expect a steeper learning curve).



Below is a guide combining and adapting both tutorials. You can follow this as a blueprint, adjusting for your parts, blade count, etc.

Step 1: Plan & design your system
Decide scale / capabilities
 - Decide how many LEDs you want (per blade or total).
 - How many blades (1, 3, 5)?
 - Do you want to display text/images, or just simple patterns?
Design blade / mount layout
 - For a thrift fan: use existing blades and mount LED strip(s).
 - For ceiling fan display style: consider cutting new blades from plywood or lightweight material (as in the Ceiling Fan tutorial). 
Instructables

 - Plan how the LED strips or boards will be placed, and where wiring will run (towards hub, slip ring, or center).
Circuit / electronics design
 - If using LED strips: you need power, ground, data (and possibly clock for some types).
 - If using custom boards / discrete LEDs: might need driver ICs (shift registers, etc.). 
Instructables

 - Plan a synchronization sensor (like a hall effect sensor + magnet) to detect when the blades complete a revolution (for POV timing). The Ceiling Fan tutorial uses this method. 
Instructables

 - Plan power supply sizing (LED current, voltage drop, etc.).
Slip ring selection
 - Choose a slip ring with enough channels (3 or 4 wires) to pass your power + data through to the rotating part.
 - For example, Light Breeze projects uses a slip ring with 3+ wires. 
Instructables

Step 2: Test basic LED wiring
Before mounting anything, wire up your LEDs (or LED boards) off the fan.
Connect to your microcontroller and run example code (e.g. from the LED library) to confirm that all LEDs light up and respond correctly. (From Light Breeze: “Hook up your light strip to your Arduino or RPi … make sure your example code runs.”) 
Instructables
If you have multiple strips or boards, test them individually, and confirm data chain works reliably.

Step 3: Prepare & solder to the slip ring
Lay out how your wiring from LED strips to slip ring will go, keeping the wires as short as possible to reduce tangling or stress. (Light Breeze recommends a dry-run layout.) 
Instructables
Cut LED strips (if necessary) to appropriate lengths. Many addressable LED strips allow you to cut at designated cut points. 
Instructables
Solder the LED wires to the slip ring wires.
 - For 3-wire strips: connect power, ground, data.
 - For 4-wire strips: you may have power, ground, data, clock (or separate data channels).
 - Be careful to wire correctly and avoid shorts.
After soldering, insulate your joints (heat-shrink, tape, or hot glue). (Light Breeze suggests wrapping or hot-glue insulation.) 
Instructables
Optionally, after soldering, test again (connect through the slip ring) to ensure signals and power still go through correctly.

Step 4: Mount the slip ring & LEDs to the rotating part
Mount the slip ring axis at the hub / center in a stable way, ensuring it is aligned (i.e. no wobble).
Mount the LED strip(s) onto the blade(s), using adhesive (super glue, hot glue, or tape), ensuring they are flat, stable, and well centered. (Light Breeze glue + tape approach.) 
Instructables
If you have multiple blades (or multiple boards per blade as in Ceiling Fan style), mount them symmetrically and route wiring toward central hub. (Ceiling Fan tutorial describes mounting boards and wiring harnesses toward center). 
Instructables
Ensure blades remain balanced. After mounting, spin the fan by hand (or run at low speed) and see if there’s vibration. If so, you may need to add counterweights (small weights, nails, etc.) to balance. (Light Breeze step: “Balance your fan blades” by gluing rocks or nails) 
Instructables
If using a ceiling fan-style design where wiring is internal toward the fan hub, route wires neatly and secure them (zip ties, channels) so they don’t snag. (Ceiling Fan tutorial uses zip ties to avoid snagging) 
Instructables

Step 5: Run wiring & mount control electronics
Drill an output hole in the fan’s front cover or hub (if using the thrift fan approach) big enough for slip ring wires / connectors to pass through. (Light Breeze says: “Drill a hole … and run the wires out.”) 
Instructables
Run extension wires from slip ring output to your microcontroller / power supply, which is stationary.
Secure the microcontroller and power supply in a safe location (e.g. base of fan or ceiling fixture).
If using a hall effect sensor for rotation detection, mount the sensor near the path of a magnet mounted on rotating part; wire that sensor to the microcontroller. (Ceiling Fan tutorial does this) 
Instructables
Double-check all wiring connections, ensure good insulation, avoid shorts, and verify no wires will obstruct movement.

Step 6: Program & synchronize
On your microcontroller, load a test sketch to drive the LED strip(s) with a simple pattern (solid color, wipe, etc.) to confirm everything is working while rotating (at low speed).
If you are doing a POV display (text, images), implement synchronization using the hall effect sensor trigger. Use the sensor’s detection of a magnet once per revolution to reset your timing loop so the LED pattern starts at the same angular position each rotation. (This is the method used in the Ceiling Fan tutorial’s Step 9 “Programming Images”) 
Instructables
Use a data structure (e.g. an array, or a mapping) that represents the LED states over angular positions; when rotation begins, output the LED states at the correct timing offset (delay) to match rotor angle.
Test and fine-tune delays and transitions so the image/text appears stable.
Gradually increase fan speed and test the persistence effect; adjust timing and brightness if needed.

Step 7: Final checks & cleanup
Run the fan at full (or desired) speed and observe stability, vibration, etc.
Tweak balance or adhesive as necessary.
Validate long-term reliability: wires should not overheat, connections should remain solid, insulation should hold.
Optionally, enclose or cover exposed wiring neatly, add safety measures, etc.
Enjoy and iterate — once basic functionality works, you can expand patterns, support animations, multiple blades, etc.



---

**Research Total: 100 / 100**

---

## **Instructions**

### **Final materials list including costs (30/30)**

| Item                              | Quantity | Cost (Approx.) |
| --------------------------------- | -------- | -------------- |
| DC Motor (fan)                    | 1        | $8             |
| Geared DC Motor (oscillation)     | 1        | $10            |
| Arduino Uno                       | 1        | $25            |
| Motor Driver (L298N or similar)   | 1        | $7             |
| Fan Blades                        | 1        | $5             |
| Power Supply                      | 1        | $10            |
| Wires, screws, hardware           | —        | $5             |
| 3D Printing / Laser Cut Materials | —        | $10            |

**Total Estimated Cost:** ~$80

### **Tools used, including hand tools and Fab Lab equipment (30/30)**

**Hand Tools:**

* Screwdrivers
* Wire cutters and strippers

**Fab Lab Equipment:**

* 3D Printer (PLA, 0.2 mm layer height)
* Laser Cutter (for base and housing panels)
* Soldering iron



* Arduino (.ino) code for motor control and oscillation
* Fusion 360 files for fan housing and base
* Laser cutter files (.DXF) for flat components

