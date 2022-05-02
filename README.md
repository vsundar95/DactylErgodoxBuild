# DactylErgodoxBuild
## Abstract
This build log details how I was able to build the Dactyl Ergodox from OhKeycaps!
Most of the parts came from the DIY Kit from OhKeycaps. The microcontrollers 
came from keebio since OhKeyCaps did not have them. I will also list the github 
repos that contain the necessary files in order to flash the microcontrollers.
Keycaps were also purchased from OhKeyCaps but were individually purchased as
separates. There are bundles for purchase but are seldom available. Overall,
this build was relatively easy once I knew where to wire and how to flash the
controllers. I highly recommend joining the discord for OhKeyCaps for any help.

## Materials
If you do buy the DIY kit from OhKeyCaps, then a majority of the items already
come included for example the diodes, the TRRS jacks, the wrist gels,
and the PCBs. I strongly 
recommend the Amoeba PCBs for this build. The make wiring easy and it looks
clean in my opinion.  

As for the wires, I bought the 30AWG wire from Amazon. Make sure to buy a 30AWG
wire stripper to make stripping wires easy. You are going to need to buy a
solder gun with solder and flux to solder the wires and the dioides to the
PCBs. As for desoldering, you can purchase copper wick or buy a desolder gun. I
will warn you the desolder gun from hakko is expensive but worth it.  

The Microcontrollers are the Elite-C. They allow me to run a USB-C cable to
my computer. 

### List of Materials for Keyboard 
* Top and bottom Dactyl Case
* 1N4148 Diodes
* Amoeba PCB Boards (Get roughly about 80 since there might be a couple defects)
* Reset switches (get the push button ones)
* TRRS Jacks
* Elite-C Microcontrollers
* 30 AWG wire and 30 AWG wire stripper
* Soldering Iron (Hakko is my preffered)
* Solder (Amazon)
* Solder Flux (Amazon)
* Desoldering gun/copper wick (Amazon)
* Zip Ties (optional but highly recommended for cable management)
* Keycaps (Can be bought from OhKeyCaps...either SA Blank or DSA Blank...prefer SA if it is available)
* Switches (I went with Kailh Royal Purple but I love the Golden Pinks as well)
* TRRS Cable
* USB-C Cable

## Instructions
Looking at the github repo: https://github.com/qmk/qmk_firmware/blob/master/keyboards/handwired/dactyl_promicro/dactyl_promicro.h we can see the wiring of the rows and columns for the dactyl ergodox. I would first
start with soldering the diodes to the amoeba pcb boards. Be mindful of the direction of the diodes when soldering them. The PCB boards call out where the negative terminal should be wired. Please do not mix up this soldering. 

#### Rows
Once the diodes are soldered onto the boards, you can start wiring the rows. I would suggest to wire the boards outside of the case for more room. Each wire can can be about 1.5 inches for the rows. That should give enough clearance when soldering the boards to the switches. 

Be mindful when wiring up the last row that L45 is the first big key in the thumb-cluster. As a matter of fact, L45 and L55 are the two big keys in the thumb cluster. You can wire up L44 to L45 as the last part of the row once you have soldered the PCBs to the switches. The thumb cluster row only has 5 maps in that row: L55, L51, L52, L53, and L54. 

#### Columns
As stated before, L45 and L55 are the two big keys in the thumb clusters. When wiring the columns, 1.5 inches of wire should suffice. Be mindful when wiring the columns that Columns 1 - 4 are associated with the remaining four keys in the thumb cluster. Column 0 does not have any keys in the thumb cluster. Column 5 has the two big keys in the thumb cluster. 

#### Wiring to Microcontroller
Looking at the imgur link: https://imgur.com/a/ugqJm8Q , you can see how to wire the PCB boards to the Elite-C microcontroller. Looking at this imgur link: https://imgur.com/a/H2j1yIw , you can see more specifically how to wire the rows and columns to the Elite-C. The second imgur link will show you how to wire in the TRRS Jack. Port D0 is the default communication port on the Elite-C for communicating between the two hands. When wiring the reset push button, it doesn't matter which pin goes to GND or RST. The button when depressed will connect the two causing a reset. 

#### Assembling The Cases
Using the zip-ties, you can tie up the cables to prevent the wires looking like spaghetti. Now screw in the top plate to the bottom plate and add the arm rest gels.

Congratulations!! You are now complete with the dactyl build!

## Software 
The two main pieces of software for this build are AVRDudess and Vial. These
software do run on Linux, Windows, and MacOS. For this documentation, I will be
writing if the user is using a Linux machine. 

AVRDUDESS: https://blog.zakkemble.net/avrdudess-a-gui-for-avrdude/ <br />
VIAL: https://get.vial.today/

I will also be adding the github repo files for the necessary flashing of the Elite-C
microcontrollers. 

LEFT EEPROM File: https://github.com/qmk/qmk_firmware/blob/master/quantum/split_common/eeprom-lefthand.eep <br />
RIGHT EEPROM File: https://github.com/qmk/qmk_firmware/blob/master/quantum/split_common/eeprom-righthand.eep <br />
DACTYL PRO MICRO Hex File: https://github.com/Oh-Keycaps/firmwares/blob/main/keyboards/handwired/dactyl_promicro/handwired_dactyl_promicro_via.hex <br />

## Flashing the Microcontroller & Keyboard Key Configuration
### AVRDUDESS
Connect your dactyl keyboard to your computer that has the software. I would suggest you connect one hand at a time. 

1. Start by opening up avrdudess.exe by typing `mono avrdudess.exe`.
2. There are two fields you need to edit: Flash and EEPROM.
3. For the flash file, use the Hex File above in the Software tab.
4. For the eeprom file, use the appropriate file that matches the hand you have plugged into your computer.
5. Now you are ready to flash the microcontroller. You might need to hit the reset key on your keyboard for the flashing to work. 
6. Repeat for the other hand

### Vial
When you download the Vial software on Linux, it will come in an AppImage. Change the permissions on the software and execute it like a script
A. chmod 777 Vial.AppImage
B. ./Vial.AppImage

Now with Vial open, check to see that all keys are configured correctly by pressing each individual key on the keyboard. 
At this point, you can create a keymap unique to your liking


## References
1. www.ohkeycaps.com
2. https://github.com/qmk/qmk_firmware
3. https://github.com/Oh-Keycaps/firmwares

