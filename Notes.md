# Fans:
- iBuyPower ARC120B V6 fans (can’t be bought, only included with specific cases)
- 120mm
- 4 fans
- 1500RPM max
- ARGB fans
- One fan’s bearing is a little tight, so it needs a higher voltage to start and doesn’t go as fast compared to other fans (still goes fast enough)
- Power: 12VDC, 0.2A max
  - Speed is controlled by the voltage, can go as low as 5V, shouldn’t go lower than 6 because of that one fan that needs a bit more power
- Typically plugs into a hub that is included with the fans. It lets you control 4 fans with 2 different fan signals and 1 RGB cable. The PCB has no electronics except for 2 diodes downstream from the fan voltage input
- The fans use a 6 pin connector, pinout:
  - GND (for fan)
  - 12V (for fan)
  - RPM sensor (not used for speed control, just lets you know the RPM)
  - GND (for RGB)
  - DIN (for RGB, uses same protocol as neopixels, planning on making everything white to help illuminate the area)
  - 5V (for RGB)

# Design:
- 2x2 grid of fans, all fans will have the same input signals (RGB and voltage)
- The RPM sensor will not be connected (could maybe go to a test point but that’s it)
- Will have USB-PD and will input 5V (makes it compatible with all chargers)
-  Should also have a USB-A port to power other devices such as the light box (pixeldust)
- Battery will be at least 1000mAh-3000mAh, ideally ~10000mAh
  - Assuming max power consumption, at 1000mAh (3.7Wh), the battery would last ~24mins
  - Assuming max power consumption, at 3000mAh (11.1Wh), the battery would last ~1hr 10 mins
    - Including the USB port drops it down to ~27 mins
  - Assuming max power consumption, at 10000mAh (37Wh), the battery would last ~3hrs 51 mins
    - Including the USB port drops it down to 1.5hrs
- The fans should be at the bottom with the “control box” (with the PCB + battery) being at the bottom towards the side of one of the fans
- Single knob controls power to the fans along with the speed
- A single switch controls power to the whole PCB
- A battery charger will need to be built-in
- A single USB-C input for power (no exposed programming ports)
- Battery cost would be ~$20 (should see if I can harvest a battery from a battery bank)
- To connect the fans, make the fan grills have screw holes at the front and a heatset insert or nut in the back. Each fan grill is separate from each fan, but there will be plates in the back that connect the fans. (Ex. A small plate in the middle will connect all 4, while there will be 2 more on each side of the fan that connects to another fan)
- The filter holder would be magnetically attached to the fan grills

# Filter:
- Carbon filter is the best idea (helps get rid of the smell, but not the actual chemicals)
  - I can also print an adapter so people can use a 100mm hose to exhaust the fumes outside, but given how much I solder, I can likely just open a window, vaguely point the fan so it intakes the smoke, filters the smell out, and exhausts it towards the window which would naturally force it out due to entropy
- Lowes has a carbon filter for ~$4 that is 15x24in wide and 1in thick. Enough for ~16 fans ($1 to replace all of the filters)

# Circuit:
- Main parts
  - USB-PD section	
    - Somewhat difficult (with current knowledge)
    - Needs to convert from 5V to 3.7V for charging
  - Battery charging section
    - Very difficult (with current knowledge)e
    - Needs to convert back from 3.7V to 5V for the RGB (maybe) and the fan (which will later be variably boosted up to 12V)
  - Fan speed controlling section
    - Should be easy (with current knowledge)
    - 5V-12V
  - MIGHT have something to make all of the lights white if it’s cheap enough (less than $3), else, no lights will be connected, power would be saved, and DIN rails will NOT be connected
    - Very easy (would need a microcontroller of some sort)
    - 5V
    - Honestly, very unlikely. Adds extra cost, increased power usage, no real benefit. Plus, pixeldust can be connected to the USB port for even better light anyways
  - USB-A port section
    - Seems easy (with current knowledge) but seems like there are some safety things to think about
    - 5V

# Battery:
- Harvested 10000mAh (37Wh) battery from USB power bank. The power bank itself doesn’t have an IC with markings that lets me know what it uses. But the battery is 4 18650 cells connected together. Should work well and should be easy enough to enclose in a separate case.
