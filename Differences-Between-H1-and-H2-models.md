The **H1** is the [original](https://github.com/eried/portapack-mayhem/tree/master/hardware/portapack_h1) design, which is well documented and in the public domain. 

PortaPack **H2** is a modification based on the last (from an unknown origin, no public design documentation available) incorporating some enhancements:

* Bigger screen
* Different navigation buttons
* Internal battery
* Battery charging circuitry
* Better internal Speaker integration

Note: _There are several H1 hybrid models on the global market including **some** of the H2 enhancements but keeping the H1 selector wheel. Some of these H1 hybrids have names similar to **2020 H1 Model**, **H1 plus**, **H2+**_

# Audio

Both feature a **headphone connector** and the **AK4951 AUDIO / CODEC IC** ([datasheet](https://www.akm.com/content/dam/documents/products/audio/audio-codec/ak4951aen/ak4951aen-en-datasheet.pdf)).

The AK4951 includes separate pins for speaker and headphone output:

*  Pins 20 (**SPP**) and 19 (**SPN**) labeled as **SP**eaker **P**ositive and **SP**eaker **N**egative (1W 8 ohm)
* Pins 22 (**HPL**) and 23 (**HPR**) as in (**H**ead**P**hones **L**eft, **H**ead**P**ones **R**ight) (16 ohm)

Upon close inspection, several differences arise:

##  H1

Only the soldering pads for an internal speaker connector header are present. The speaker +/GND signals on the pad are routed directly into AK4951 pins.

**NOTE:** _There is no extra amplifier IC between the speaker pad and the AK4951. The AK4951 includes a speaker amplifier capable of 1W, when powered @5v._

**You can solder a laptop / tablet speaker in H1 speaker pads.** In order to enable it, you will need to install MAYHEM firmware, where you can also configure under **OPTIONS -> INTERFACE** the addition of a SPEAKER button on your top status bar.

## H2
PortaPack H2 circuitboard includes a connector header for easily adding an internal speaker. 

The **AK4951 IC** has been rotated by 180º and placed more into the middle of the circuit board, allowing for the addition of an extra IC: The ChipStar brand **CS8122S** ultra-low EMI, filter-free, class-D amplifier, for driving the speaker output with up to 3W. 

The speaker audio header is switched on/off by the headphone female connector, which includes the usual mechanical switch, detecting the insertion of a male plug in it.

This is a non trivial difference, compared against H1 design where the speaker out pads are routed to the actual speaker out pins on the AK4951. On H2, the audio comes from the Headphones output pins of that IC.

Since the firmware is shared between H1 and H2, on PortaPack H2 you end up powering TWO speaker amplifiers: The one inside AK4951 CODEC IC, and the extra 3W speaker amplifier.

## H2+ Variations
At least some of the PortaPack "H2+" variations have the following audio differences:

A **WM8731** audio CODEC may be installed in place of the **AK4951**.  The WM8731 IC has no speaker amplifier, for one difference.

An **INS8002E** or **LTK8002D** audio amplifier may be installed in place of the **CS8122S**.

On some H2+ variations, audio volume is low, and inserting a headphone plug does not electrically disable the speaker output (without [additional hardware modifications](https://github.com/eried/portapack-mayhem/wiki/H2-Plus-speaker-modifications)).

# Power Supply

## H1 
There is no internal battery on your H1 PortaPack: You will need to power it up externally, from your computer or an USB powerbank.

H1 PortaPack design does NOT include any battery charging circuit, nor a provision for a power on/off switch.

Some enthusiasts managed to MOD their H1's by adding a standard usb powerbank management circuit board with the corresponding Li-ion battery and placing a manual power switch on their cases.

## H2 and "H2+"

H2 includes an internal Li-Ion battery, standard battery charging / management IC (located at the side of the speakerphone connector) and power switch.  
The power switch / battery level feature were provided by ``IP5306`` or similar module.  