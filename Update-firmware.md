In theory, it is impossible to brick the device, since you can always try the DFU recovery procedure. However, the updating might become fiddly in certain conditions.

# Normal procedure

## Firmware
Get the latest firmware from the [![GitHub release (latest by date)](https://img.shields.io/github/v/release/eried/portapack-mayhem?label=Releases&style=social)](https://github.com/eried/portapack-mayhem/releases/latest) page. Please check the [FAQ](https://github.com/eried/portapack-mayhem#frequently-asked-questions) if you have any additional question.

### HackRF/PortaPack itself via Flash Utility

The [Flash Utility](https://github.com/eried/portapack-mayhem/wiki/Flash-Utility) can also be used to program new firmware from a bin file stored on a MicroSD card, mentioned below.  The Flash utility is the update method of choice for users that may not want to run an app on their PC, or may want to switch between firmware versions when in the field.  If you download and unzip the latest mayhem_v#.##_COPY_TO_SDCARD.zip contents to your SD card, the latest firmware image will be found in the FIRMWARE folder (this method also updates the external apps in the APPS folder, mentioned below).

### Windows

1. Connect the device via USB
2. Switch to HackRF mode via the on-screen option (in the PortaPack)
3. Double click `flash_portapack_mayhem.bat` and follow the instructions
4. Reboot the device

### Linux

**For Ubuntu and Mint user: Ubuntu based distro never maintains their repo for hackrf package. You’ll face a lot of weird problems if your hackrf is R9.**
**To resolve these, please compile hackrf package yourself, or use other distro.**

1. Connect the device via USB
2. Switch to HackRF mode via the on-screen option (in the PortaPack)
3. Upload the firmware with `hackrf_spiflash -w new_firmware_file.bin` (eg. portapack-h1_h2-mayhem.bin for mayhem firmware or hackrf_one_usb.bin for stock hackrf firmware)
4. Reboot the device

### MacOS

_HackRF CLI tools for MacOS available through MacPorts or Homebrew_

1. If necessary, install the HackRF tools: `brew install hackrf`
2. Connect the device via USB
3. Switch to HackRF mode via the on-screen option (in the PortaPack)
4. Upload the firmware with `hackrf_spiflash -w new_firmware_file.bin` 
5. Reboot the device

## MicroSD card files

Your PortaPack has a slot for a memory card. You need to provide a MicroSD with enough space (16GB is recommended, over 32GB will be omitted due the limits of the FAT32). This is necessary for certain functionality, like the world map, GPS simulator, external apps, and others. 

Get the latest files from the [![GitHub release (latest by date)](https://img.shields.io/github/v/release/eried/portapack-mayhem?label=Releases&style=social)](https://github.com/eried/portapack-mayhem/releases/latest) page. You need to uncompress (using [7-zip](https://www.7-zip.org/download.html)) the files from `mayhem_vX.Y.Z_COPY_TO_SDCARD.7z` to a FAT32 formatted MicroSD card. 

### External Apps

External apps (.ppma files placed in the APPS folder of the MicroSD card) will only function if their version matches the firmware version. Be sure to update these files also when updating firmware.

# Troubleshooting

Please check [this guide](Update-firmware-troubleshooting).

Otherwise if you have a HackRF-One R9 and the instruction here do not seem to work, you may need to follow the instructions in this link.
https://hackerwarehouse.tv/product-knowledgebase/portapack-h2/hackrf-one-r9-and-portapack-compatibility/