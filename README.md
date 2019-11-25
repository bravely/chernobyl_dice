# Chernobyl Dice

<p align="center"><img src="/images/chernobyl_dice.jpg"></p>

## Introduction

#### Description

The Chernobyl Dice is a true random number generator that uses nuclear decays from a weakly radioactive sample
as a source of entropy. It consists of four primary components:

* An Arduino Nano microcontroller
* A Geiger counter
* Six uranium glass marbles
* Nixie tube display

Geiger counter events ("clicks") are converted into random bits by taking the mod2 of the total number of
miliseconds that have passed since the device was switched on (e.g. the device outputs a "0" if the
Geiger tube triggers on an even milisecond, and output a "1" if it triggers on an odd milisecond).

1. In a ring buffer, record either a 0 or a 1, depending on whether or not a Geiger event occurred
2. Debias this 0-dominated stream into an ubiased stream using von Neumann's method [0]

The uranium glass sample is illuminated by an array of ultraviolet LEDs at each Geiger event, which makes them
fluoresce bright green. This has nothing to do with the radioactivity of the sample, but it does, however, *look
really cool*.

#### Operation

The device has three modes of operations, which can be selected via the rotary switch:

*Clock Mode*

Displays the current time, with the Geiger board unpowered. The time can be set by flipping the toggle switches on and off
(the '16' toggle increments the hour, the '8' toggle increments 10 minutes, the '4' toggle increments 1 minute, and the
'1' toggle resets the seconds).

*Streaming Mode*

Repeatedly generates random numbers of a size specified by the toggles (or random bytes from 0-255 if no toggles are set). Numbers
generated in this mode are transmitted over serial via USB. This mode also has a "turbo" setting to facilitate statistical testing,
which can be enabled by holding down the pushbutton. When "turbo" is enabled bit generation will be indicated by LEDs in the
display, and the Geiger "clicks" will be silent.

*Dice Mode*

In dice mode random number generation is initiated via the pushbotton, and the size of the random number to be generated is set
by the sum of the toggled switches (no switches are set the device will generate random byte in the range 0-255). Press
once to generate the number, and once again to clear the display. The size of the number to be generated is displayed in
blinking digits.

## Overview and Parts List

*WARNING: These instructions and resources are not polished and are somewhat untested. This is a project for advanced makers, and
you should fully expect to have a bit of an adventure while building your own Chernobyl Dice! That said: Shoot me a message if
you run into trouble, and I'll try to help you out and improve the instructions as well.*

<p align="center"><img src="/images/parts_list.png"></p>

Here's a rough outline of the steps required for assembly:

1. Print or fabricate the following custom parts from files in the GitHub repository
    * Enclosure (using 3D printer or 3D printing service)
    * Logic, Nixie Display, and Control Panel Custom PCBs (using a board fabrication service such as OSHPark)
    * Stainless steel front panel (using a service such as OSHCut)
    * Acrylic back panel (using a service such as Sculpeo)
2. Order other components (see URLs in the parts list)
3. Embed brass standoffs into enclosure (this is how front and back panels and custom PCBs will be mounted)
    * TIPS
      * A single drop of cyanocrylate (Super Glue) should be placed in the standoff holes in the enclosure before they are pressed
        in (the tip of a Phillips head screw driver workds well for this task)
      * If the tops some holes came out of the printer a bit distorted then they can be widened easily by twisting a largish
        Phillips head scewdriver in them until the top of the hole is wide enough.

| Location | Standoff Length | Type |
|---|---|---|
| Rear of enclosure | 10 mm | Female-Female |
| Front of enclosure | 10 mm | Female-Female |
| Nixie Display Board mount | 10 mm | Female-Male |
| Logic Board mount | 10 mm | Female-Male |
| Logic Board-to-Geiger Board | 10 mm | Female-Male |
| Geiger Board-to-Bottom of Uranium Sample Box | 10 mm | Female-Male |
| Bottom of Uranium Sample Box-to-Top of Uranium Sample Box | 10 mm | Female-Male |
| Top of Uranium Sample Box-to-Front Panel | 10 mm | Female-Female |


4. Assemble custom PCBs and 'exixe' nixie tube driver boards using build photos as a guide
    * TIPS
      * The female headers on the Nixie Display Board for the nixie tube driver PCBs can be assembled using only four long female
        header strips (e.g. there's no need to separately attach sixteen 7-pin female headers---see photos)
      * The "CS" 8-pin male header is a currently a tight fit, so you will probably need to use needle noise pliers to push the pins
        through the board
      * For the control panel PCB you can temporarily mount the toggle switches in the front panel and then press the PCB on top of
        the back of the switches to ensure good alignment---you can then pull the whole board-and-toggle assembly off of the front
        panel to solder it, or even solder it in place and then pull it off
      * The file 'nixie_jig.stl' is a provided as a useful place to rest the nixie tube while soldering them to the 'exixe' driver
        boards
5. Attach the acrylic back panel and panel mount USB cable to the rear of the enclosure
6. Mount custom PCBs inside enclosure and perform wiring (see wiring schematic and build photos)
7. Partially dis-assemble rotary switch to attach it to the "lock plate" (lock_plate.stl)
8, Mount toggle-and-PCB assembly, LED-with-holder assemblies, rotary-switch-and-lock-plate assembly, and pushbutton on front panel
    * TIP
      * While attaching the LED to the holder, apply a drop of cyanocrylate (SuperGlue) to prevent the LED from falling out of the
        front of the holder
9, Perform wiring of the control panel (see wiring schematic and build photos)
10. Fit the eight nixie display driver boards into the female headers of the Nixie Display Board
11. Wire the Control Panel to the Logic Board
12. Mount the front panel to the enclosure, taking care to insure that the hole in the rotary switch lock plate lines up with the
    upper-left standoff on the front of the radioactive sample holder

## Wiring Diagram

<p align="center"><img src="/images/chernobyl_dice_wiring_schematic.jpg"></p>
<p align="center"><i>How connect the internal wiring of the Chernobyl Dice.</i></p>

## Build Photos

<p align="center"><img src="/images/build/small/1.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/1.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/2.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/2.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/3.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/3.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/4.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/4.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/5.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/5.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/6.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/6.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/7.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/7.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/8.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/8.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/9.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/9.JPG">Click here</a>
for larger photo.
</i></p>

<p align="center"><img src="/images/build/small/10.JPG"></p>
<p align="center"><i>
<a href="https://raw.githubusercontent.com/nategri/chernobyl_dice/master/images/build/large/10.JPG">Click here</a>
for larger photo.
</i></p>

## References

[0] https://en.wikipedia.org/wiki/Hardware_random_number_generator#Dealing_with_bias
