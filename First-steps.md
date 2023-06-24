# Identify your device

There are many different versions of the PortaPack. It is important that you identify the correct version as this can affect how you install the firmware and device initial start-up. It is recommended you read the description of versions [here](PortaPack-Versions). The H2 and H2+ versions are a slightly improved version, but the people making this copies never published the circuit diagrams or Code , hence breaking the license terms. 

The main difference are the controls and the screen size  along with the codec and processor chip. The H2 / H2+ has extra circuitry to manage the battery charging and powering on/off. In this document, there is a brief description about the details. Check a more technical comparison [here](Differences-Between-H1-and-H2-models).

# Up to date information
There is a Discord server ["HackRF PortaPack Mayhem"](https://discord.gg/tuwVMv3). This has all the current talk and information.

# Power on/off
The original H1 powers instantly when you plug a power supply to the USB port. To turn it off, just unplug it. Similar to the issues with some USB cables while [upgrading the firmware](Update-firmware), the quality of your cable might affect the performance. 

To power on/off the H2, you need to hold the middle button (knob or pushbutton) for few seconds. See more details [here](https://github.com/eried/portapack-mayhem/wiki/Powering-the-PortaPack).

For some H2+, click the knob to power on, double-click the knob to power off. 

# Extra functionality (H2 and H2+)
## Charging
This version can charge the internal lipo battery via the USB. There is a led indicator that turns off when the charging is done, but it might flicker.On some models (H2+) there are 4 leds below the knob that represent the state of the battery charge 25%,50%,75%,100%.When charging one will flash dependant on the current charge state of the battery. See more details [here](https://github.com/eried/portapack-mayhem/wiki/Powering-the-PortaPack). 

## Battery life
An internal battery between 1000 and 2500 mAh should last several hours of use, depending App use. The standby consumption is [very low](https://github.com/eried/Research/blob/master/HackRF/PortaPack/h2_standby_consumption.jpg), around 52 µA, so you do not need to worry to remove/disconnect the battery in normal circumstances.

# About firmwares
If you bought a standalone HackRF, it probably came with the GSG firmware flashed onto it. This enables usage over USB from a computer.

When buying pre-assembled HackRF + PortaPack bundles, they typically come with some version of the Mayhem firmware, but one important thing to understand is : the firmware is always flashed on the HackRF board, PortaPack has no flash nor CPU, is basically an interface module that enables standalone usage without a computer. It provides LCD screen, buttons,audio codec IC, SD card slot,a coin cell to preserve settings and time between usages, some versions a high precision clock signal and a battery.

Although the Mayhem firmware gives you the possibility to directly use a lot of functions on the field standalone , without a computer, it also provides a “HackRF mode” which enables the user to start a version of the original GSG firmware and use your HackRF via USB, controlled by a computer. However if you separate the two boards, you wont be able to use the menu GUI and enable “HackRF mode”, so if you want to use your HackRF board alone (detached), that way you'll need to flash it with the GSG firmware.

In case you bought a PortaPack separately or want to upgrade your firmware, check out our [Update firmware](https://github.com/eried/portapack-mayhem/wiki/Update-firmware) page!