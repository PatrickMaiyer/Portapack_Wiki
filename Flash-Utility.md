This application allows you to install a new firmware on your PortaPack.  The Flash utility is the update method of choice for users that may not want to run an application on their PC, have compatibility issues with their OS, or may want to switch between firmware versions when in the field.

# The Flash Utility

* **Step 1:** Compile or download the image. For example the latest nightly build from https://github.com/eried/portapack-mayhem/releases.  If you download and unzip the latest mayhem_v#.#.#_COPY_TO_SDCARD.zip contents to your SD card, the latest firmware image will be found in the FIRMWARE folder (this method also updates the external app files in the APPS folder as well as data files needed for other apps).
* **Step 2:** If you download only the file mayhem_v#.#.#_FIRMWARE.zip, extract the portapack-h1_h2-mayhem.bin file and place it in the FIRMWARE folder of your SD card.  (The SD card may be physically plugged into your computer, or left installed in the PortaPack using the "SD over USB" app and connected with a USB cable.)  See note below regarding external apps.
* **Step 3:** Start the Flash Utility and select the new .bin file.

**NOTE:** If original firmware running on your portapack is version 1.9.2 or later, it has a Flash Utility that supports ppfw.tar files that contain the firmware image plus all external apps.  In this case, you only need to download the one file mayhem_v#.#.#.ppfw.tar and place it in the FIRMWARE folder of your SD card.  When you select this file in the newer Flash Utility, the Flash Utility will automatically extract all the external apps to the APPS folder and flash the firmware .bin file.

![grafik](https://user-images.githubusercontent.com/13151053/228267608-cf281412-151d-4405-95d9-300c266e26c9.png)

![SCR_0009](https://user-images.githubusercontent.com/13151053/228262638-db3c7d7e-e4ba-400f-8037-10969fc1b382.PNG)

* Step 4: Select Yes

![grafik](https://user-images.githubusercontent.com/13151053/228263095-8e968306-fb11-4312-8a63-802bdc84ed54.png)

* Step 5: Watch the LEDs blink and wait the 15 seconds.  If your original firmware was version 1.9.0 or later, the portapack will automatically reset itself after the new firmware is installed.  Otherwise:
* Step 6: Double press the knob to turn off the portapack.
* Step 7: Press the knob to turn on the portapack. You should now have the new firmware installed.

## External apps
The version of any External Apps must match the version of the currently running firmware.  If only the main firmware is updated, old external apps in the APPS folder of the SD card will not run.  See note in Step 1 above.

# If things go wrong
Sometimes something goes wrong and you are in a state where the portapack refuses to turn on again. You should know that no matter what you do, you can always recover from such situation. The portapack has a dfu that can never be deleted / overridden and should be used in this situation: [Update-firmware-troubleshooting](Update-firmware-troubleshooting)