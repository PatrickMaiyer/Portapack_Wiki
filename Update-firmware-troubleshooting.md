One of the main sources of problems while [updating the firmware](Update-firmware) is the quality of the USB cable. Try with several ones just to be sure before trying any other solution.

## Black or white screen?

If you get a black or white screen after updating, please check the wiki here: [Won't boot](https://github.com/eried/portapack-mayhem/wiki/Won't-boot)

## An application is not starting anymore?

Maybe an update in the application settings broke the settings file for the app. Just go in the SETTINGS folder at the root of the SD card and delete the related settings file. As an example lets take the audio app: if we follow the previously mentioned method, then we just go and delete the rx_audio.ini file in SETTINGS directory. This will force a new settings file to be generated with all new needed parameters at the next attempt to launch the app.

## Update failed on Ubuntu/Mint/Ubuntu based distro?
For Ubuntu and Mint user: Ubuntu based distro never maintains their repo for hackrf package. You’ll face a lot of weird problems if your hackrf is R9.  
To resolve these, please compile hackrf package yourself, or use other distro.

## DFU

This is a special mode to update the firmware in case of problems. To enable this, you should reset your device holding the RESET and DFU buttons at the same time, while doing this, release RESET, and then release DFU. The leds should be ON and the screen wont show anything.

> Sometimes it’s tricky to entering DFU mode, here is some way to entering it if you have no luck with the method above:  
>W1. Press and holding DFU button, then plug the USB cable, then release the DFU button.  
>W2. Press and holding DFU button, then single press the knob, then release the DFU button, then plug the USB cable.
>W3. Plug in USB. Press and hold DFU button and unplug USB. Release DFU button and plug USB back in.


### Windows
If you are in Windows, from the release package double click `dfu_hackrf_one.bat` and follow the instructions. Do not disconnect or reset your PortaPack after that procedure, continue in the step 3 of the [normal procedure](Update-firmware#normal-procedure).

### MacOS
_DFU Utils CLI tools for MacOS available through MacPorts or Homebrew_

1. If necessary, install the DFU tools: `brew install dfu-util`
2. Connect the device via USB
3. Switch to DFU mode as per the section above: *DFU*
4. Upload the firmware with `dfu-util --device 1fc9:000c --download hackrf_one_usb.dfu --reset` 
5. Reboot the device

### Linux
_DFU Utils CLI tools for Linux available in standard repositories_

1. If necessary, install the DFU tools (example for Debian/Ubuntu variants): `sudo apt install dfu-util`
2. Connect the device via USB
3. Switch to DFU mode as per the section above: *DFU*
4. Upload the firmware with `dfu-util --device 1fc9:000c --download hackrf_one_usb.dfu --reset` 
5. Reboot the device

### Alternative environment

You may be able to try in a virtual environment, completely isolated from your current OS:
1. Download http://eu2-dist.gnuradio.org/ and burn the ISO and boot from it, select the LIVE Image
2. Once in the environment, Open a Command Prompt and type: `sudo apt-get install dfu-util`
3. Connect your device to your computer
4. Press RESET and DFU buttons at the same time, and while doing this, release RESET, and then release DFU
5. Open a terminal and type `dfu-util --device 1fc9:000c --download hackrf_one_usb.dfu --reset`
6. After that, without disconnecting it, you can upload the firmware with `hackrf_spiflash -w new_firmware_file.bin`

## Notes

If you have an existing HackRF One and you've acquired a Portapack separately (from third party suppliers), do the following:
1. Make sure you flash the HackRF One first before attempting anything with the HackRF One + Portapack combo. The code to run Portpack comes from the HackRF One firmware as flashed. 
2. If you don't flash the HackRF One and just plugged in the Portapack and powered up the setup, the screen on the Portapack will flash and nothing else will be seen. This does not mean that the Portapack is faulty.
3. After flashing the HackRF One, you can plug in the Portapack and when the setup is powered up. you will see the screen show the UI for the version of the firmware that was flashed into the HackRF One. 

## Video
The following video explains all possible outcomes while trying to update the firmware and possible mitigations:
https://www.youtube.com/watch?v=_zx4ZvurgOs

There is another very good video about the general overview, also including the update procedure:
https://www.youtube.com/watch?v=kjFB58Y1TAo

# Still stuck?
If you still experience problems after reading this and checking the video, submit an [issue](https://github.com/eried/portapack-havoc/issues/new?assignees=&labels=&template=problem-upgrading-the-firmware.md&title=Problem+upgrading+the+firmware).

Also, there is a lot more details on the [HackRF wiki](https://github.com/mossmann/hackrf/wiki/Updating-Firmware).