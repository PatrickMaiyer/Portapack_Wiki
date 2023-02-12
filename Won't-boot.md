# My device wont start up

## White screen
If you device won't boot and leaves you on white screen, then you will need to power off the device and then hold down the **UP** button while you power it on. This could take up to 10 seconds.

If this does not work, then try the same thing but this time holding the **DOWN** button (Remembering to wait up to 10 seconds).

What this is doing is loading a different LCD driver to get your devices screen to work.

Once that is done you should be able to reboot normally without any issues.

## Black screen
If you device won't boot and leaves you on a black screen, then you will need to power off the device and then hold down the **LEFT** button while you power it on. This could take up to 10 seconds.


# Description
* UP key = LCD driver 1
* DOWN key = LCD driver 2
* OK/SELECT key = Reset/Automatic detection
* LEFT key = LCD driver 2 QFP100 chip
* RIGHT key = LCD driver 1 QFP100 chip

_**Note:** H2+ usually require you to hold the **UP key** on the first boot to configure them._

_This is valid from nightly version **n_220412** and stable release version: **v1.5.1**_

# H2+ (and H1) not powering up , just black LCD:

(1) disassemble both boards . (your mileage may vary: for an H2+ it is mandatory , because you can not activate DFU with both boards assembled, and in case of H1, no need to disassemble).

(2) pick up your hackrf, connect it to USB, If it's not bricked and you have a green LED, if H2+ flash it with special fw jumbo77 1.43, if H1 use official fw 1.43. If it is bricked (no green LED), you will need to flash these via DFU.

(3) assemble boards , confirm correct power up. At first power up, keep pressing the appropriate button for your unit for more than 2 secs, until getting correct LCD display.

(4) put the device in hackRF mode and flash latest Mayhem firmware.

## Explanation
Firmware starting at version 1.5.4 and onward contain the <a href="https://github.com/eried/portapack-mayhem/pull/662">Pull Request 662</a> that uses the persistent memory to test and store the hardware and LCD config settings . That memory uses the same back up voltage than the Real Time Clock calendar, both needs a healthy cell battery button voltage. Sometimes, in a re flashing process , although we got good battery cell button voltage, the unit seems to be badly initializing those persistent bytes and we got strange black screen. Doing those above steps probably reset the persistent memory. That's just a guess.
