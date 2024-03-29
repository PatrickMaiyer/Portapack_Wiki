The SD Card provides a memory resource that can be tailored to the specific user. Technical details of the card are given [here.](https://github.com/eried/portapack-mayhem/wiki/SD-Card-(DEV)) The SD card Standard image is supplied as part of the standard firmware download. Instructions for its use are supplied elsewhere. The SD card holds information in relation to Specific Apps or as general list of items such as frequencies follows:

* **ADSB:** The ADBS Folder has databases of Airlines, IACO and is where the world map is located. See separate page on how to generate the map.
* **AIS:** Holds the AIS database.
* **AUDIO:** Holds audio recordings (WAV) from the Audio app.
* **CAPTURES:** Holds IQ capture files (C16/C8 and their metadata TXT files) from the Capture app.
* **DEBUG:** Holds various debugging log files.
* **FIRMWARE:** bin files can be placed here and used to update the PortaPack firmware without a computer.
* **FREQMAN:** Holds FreqMan DB files which are lists of frequencies that can be loaded by various apps. They can be viewed and edited using the FreqMan app.
     *  **Fixed frequencies in Apps:** It should be noted that in some Apps that the frequency ranges are fixed in the App and are not selectable in from FREQMAN lists. Example of this are "AIS" and TPMS.
* **GPS:** This file holds information on how to generate GPS-Simulation files.
* **LOGS:** Holds log files for various apps like ADSB or POCSAG.
* **LOOKINGGLASS:** This folder holds a text file that is used in the LOOKINGGLASS App and is a list of the frequency scan ranges  and a description. It should be noted that this APP can have only have ranges that are a minimum of 240MHz in size.In addition the range must start form 10MHz. the nominal Minimum operational frequency of HackRF. Therefore you need to consider this in planning the frequency range listed. For example you could not have a range for  VHF amature band , You can only have a range from 10-250 MHz. These are very wide ranges  in keeping with the Ap concept of Wide Scan of the spectrum.
* **PLAYLIST:** Holds playlist files (PPL) for the Replay app.
* **REMOTES:** Holds remote files (REM) used by the Remote and TouchTune apps.
* **SAMPLES:** Holds an example of some settings for the use in OOK TX App
* **SCREENSHOTS:** Holds screenshots (SCR) taken on the device.
* **SETTINGS:** Holds settings for applications. If you're having a problem with an app, try deleting its settings file to restore defaults.
* **SPLASH:** Holds custom splash screen BMP files.
* **SSTV:** Holds some Standard Images for the use in the SSTV app.
* **WAV:** Holds sound files that are used in the SoundBoard app.
* **WHIPCALC:** Holds information on the  Whip lengths that are used in the App calculation. Additional Whips can be added with their specific details.
