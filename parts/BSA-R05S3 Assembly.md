# BSA-R05S3 Assembly Instructions

Start here if you've bought a DIY kit and are ready to assemble! If this is your first time soldering SMD components but have THT experience, go slowly and you'll be fine. 0805 sized components are very manageable with tweezers, and advice on technique is included below.

Dozens of tester boards were assembled with a C2 sheep's foot tip, you will not need any specialty soldering tools.

## Preparation and Tools

You will need:

- Soldering iron
- Small-medium soldering tips (B2/C2 recommended)
- Safety glasses
- Well ventilated space
- Solder (0.6mm recommended)
- Paste or pen flux (Paste w/ syringe recommended)

Optional:

- Hot plate
- Solder paste (180 C recommended)
- Antistatic bracelet

## Setup

If working with an ESP devboard, connect via USB/serial and flash a blink or similar firmware to test for proof of life. If working with a bare ESP chip carrier module, flash with a burner rig or solder straight to the board. We have not had any DOAs from current suppliers, you should not have any issues if the carrier module is oriented correctly.

Lay out parts for step by step assembly:

1. Resistors (3)
2. Capacitors (5)
3. AMS Regulator (1)
4. Switches (6)
5. USBC Header (1)
6. ESP32 (1)
7. ATG336 (1)
8. MicroSD Reader (1)
9. Molex Header (1)
10. Molex 4-pin Wire Harness (1)
10. Buzzer (1)

## Assembly (Hand Soldering)

1. Keep away from stray wires fragments, power sources, etc
2. Start with the ESP32. Position in the center pads with the antenna to the LEFT
3. Apply flux to the castellated pads and PCB pads. Postion the ESP correctly, and hold it down with one finger. Get a good blob of solder on your iron, and solder one of the corner pads down. Do the same on a far diagonal corner pad (doesn't matter which, this is to lock the position and free up your hands).
4. While feeding solder to your iron, drag it down the side of the MCU. 0.6mm solder is pretty forgiving, you should not get any conjoined pads. If you do get conjoined pads, add a little more flux and do another pass without feeding solder and it should redistribute itself. If you have several conjoined pads, clean your iron as you go so it can collect the excess.
5. Next, do capacitors. Go one by one, they have a tendency to jump if you place them all at once. They are not polarized, you can add in any orientation.

Add flux to the pad, then place the capacitor. Use closed tweezers to apply pressure from the top once placed. Do the blob transfer method as with the corner pads on the ESP, solder one side, then the other while applying pressure. Get the temp high enough to get the solder to transfer within a few seconds to avoid reflowing both sides and accidentally moving the capacitors.
6. USBC connector. The USBC connector will go through the front of the board so you can solder from the back. Align and tilt in the rear pins, then apply a little pressure to the front legs to snap it in. Flip back over to the ESP side. Apply flux to the pins and legs. Solder the front and back legs in. Apply solder to the pins with a small circular motion, you do not need to try to do them individually, the flux will prevent bridging. Flux in the through holes needs to gas out so the solder can flow in. Do a first pass, then do a second slower pass, adding solder as needed as any remaining flux gasses out and the solder flows in.

If you cannot connect to the ESP after assembly, reflow the USBC header again to make a better connection, and check for bridging. These are the most common issues when hand soldering USBC headers, almost always resolved with a reflow.
7. Resistors and AMS-1117. Same method as capacitors, start with the two resistors near the USBC header (5.1k). Next add the 10k by the reset buttons, then do the AMS. Too much solder can make the resistors tilt up and short or connect poorly. Apply downward pressure for both joints. Do these after the USBC so you have plenty of room.
8. Molex header. Orient the header so that the red wire is on VBUS when connected. Solder the molex header in from the front, make sure not to bridge the connections.
9. Switches. Do both the back and front. Flux the pads and solder on, these should be easy after doing the caps and resistors. They are non-polarized and can be added in any orientation.

*** You can now connect to the ESP over USB. Plug in the molex, and connect the red and yellow wires temporarily for power, leave white and black disconnected. Connect and run `esptool chip-id` to make sure everything is wired in and the chip is responsive. If esptool cannot connect to the MCU there is strange behavior, reflow the USBC header and 5.1k resistors and try again.
10. ATGM336 and microSD. Place the pins through the through holes, then place the modules on top. The antenna connection on the ATGM is UP. Get it roughly level, do both ends, then work the middle. The microSD reader has the PCB facing UP (dead bug). Check pin labels, then solder the same way. The microSD can be level or leaning on the board, the case opening is large enough to accommodate either. Snip the excess length on the screen side of the board as low as possible.
11. Flip it over. Do the buttons now if you have not already.
12. Front LED. First apply some kapton or vinyl electrical tape to the DO pins on the LED carrier, to avoid shorting the in and out pads. There are three ways to solder the LED:
    A: If you have a hot air rework tool, the easy way is to apply low temp solder paste to the pads, gently squish the LED down, and apply heat to the exposed length of the PCB pads while protecting the LED with kapton or a putty knife.
    B: If you only have a soldering iron, take the three extra straight pins and solder them to the LED backer. Once attached securely, gently remove the plastic spacer. Place the LED on the PCB pads, and solder the pins down.
    C: (Fiddly) Apply light solder to one PCB pad, keep the iron on the pad, and position the LED. Wait for the LED pads to warm up and bond (2-3 seconds). Remove the iron, allow to cool for a few seconds, and test the hold. If not attached, reattempt. Once firmly secured, flip over, and solder from the back using the through holes
12. Buzzer. Align + and - to the silk screen, solder from the back side
13. Screen. Last piece! Use the included spacers to keep it parallel to the board and prevent contact with any THT components. Tape over any THT components if desired. Solder in.

Hardware assembly is done! Connect over USB again to confirm ESP is reachable and working, you are 90% of the way to wardriving for Flocks and other surveillance devices.

Grab the appropriate STLs for your generation of hardware, and start the print while you work on flashing.

Head over to https://github.com/LoneCrowDesign/birdoscope-firmware to begin flashing