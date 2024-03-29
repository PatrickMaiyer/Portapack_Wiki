## Memory 
Gives the information on the memory used by  M0  core.
## SD Card 
Gives information on the SD card and allows it to be tested.
## Peripherals
Gives information on the peripherals:
* RFFC5072
* MAX2837
* SI5351C
* WM8731 or Ak4951 (depending on the IC audio codec detected in your PP brd)

![DD1FEF74-140D-4B9E-B86C-B658B035919D](https://github.com/eried/portapack-mayhem/assets/86470699/272500d6-413d-4fcb-9bd6-73b44caa7f1d)

![00403D10-E202-4014-A4C5-B36A216AC548](https://github.com/eried/portapack-mayhem/assets/86470699/a3d9529f-d379-46d0-b326-7cbc020a62a4)

Note : Recently (Manufacturing year: 2023) GSG introduced the new r9 Hackrf board version (already compatible with Hackrf and Portapack-Mayhem fw's).

![image](https://github.com/eried/portapack-mayhem/assets/86470699/7a1c98ce-8f88-4305-bb51-620a2e8add93)



That new Hackrf board revision r9  has two 2 IC’s changes: 
* MAX2837 was replaced by MAX2839. 
* Si5351C was replaced by Si5351A with additional clock distribution. A series diode was added to the antenna port power supply. 

Starting with HackRF One r6, hardware revisions are detected by firmware and reported by hackrf_info.

Thanks to GSG developers and our Mayhem git admin , we merged their commit about all those r9 hw support in our Portapack Mayhem Debug menu tool. And now  you can also easily detect that r9 version without disassembling  the boards :
 
![image](https://github.com/eried/portapack-mayhem/assets/86470699/49b1d3f2-d7c7-4940-8d18-c49293f2b8ab)


## Temperature 
Data is provided by the MAX 2837 (or MAX 2839)  on chip digital temperature sensor. The accuracy is quoted as 4.33°C per value.

## Buttons Test
This shows when either the buttons are pressed, the encode knob is turned or the screen is touched. It can also show if the encoder when turned is cleanly stepping the states as it is turned. Encoder sensitivity is now adjustable in Settings, and the encoder can be desoldered and replaced with a better-quality version if it has issues.  The test screen also has an option for testing the "long press" feature which is applicable to the directional keys and the DFU switch only.

![SCR_0013](https://github.com/eried/portapack-mayhem/assets/125336/1415257f-e322-428c-801d-71977603640e)

## Touch Test
Allows testing the Touch Screen calibration (and your artistic skill) by drawing on the screen using a stylus. The following controls are available:
* Select key returns to Debug menu.
* Left key changes the pen to a random color (hold in the button to rotate through them faster); this can also be done while drawing.
* Down key clears the screen to a random color (like shaking your Etch-a-Sketch).
* Turning the Encoder dial changes the pen size.

Note that the screen-shot icon is still active but hidden (it will become visible if that spot of the Touch Screen is pressed).

## P. Memory
Displays the contents of the persistent memory area. (256 bytes)

It is split into three pages, pages can be changes with the encoder and the current offset from the start of p.mem area is displayed on the top: "XX+" Also on the last page theres some padding with FFs displayed after the p.mem area ends.

At the bottom it displays also the current size of the data_t struct (this is what we persist into p.mem) and the currently stored checksum (it is calculated from the first 252 bytes of the p.mem area when changes are made to the settings and then written to the last 4 bytes of p.mem)

The version of the stored config isn't displayed separately but it can be seen as the first 4 bytes of the p.mem area.

## Debug Dump
Writes a file containing debug information to the DEBUG folder.

## M0 Stack Dump
Writes a file containing M0 stack contents to the DEBUG folder.

## Fonts Viewer
Displays the 5x8 and 8x16 font character set.  (Firmware version 1.7.4 only)
