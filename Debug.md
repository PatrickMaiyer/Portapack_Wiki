## Memory 
Gives the information on the memory used by  M0  core.
## SD Card 
Gives information on the SD card and allows it to be tested.
## Peripherals
Gives information on the peripherals:
* RFFC5072
* MAX2837
* SI5351C
* WN8731
## Temperature 
Data is provided by the MAX 2837 on chip digital temperature sensor. The accuracy is quoted as 4.33°C per value.
## Buttons Test
This shows when either the buttons are pressed, the encode knob is turned or the screen is touched. It can also show if the encoder when turned is cleanly stepping the states as it is turned. Note on cheep portapack clones of the encode that is 24 step version can be over sensitive and miss steps. It can be changed with a better-quality version.
![SCR_0013](https://github.com/eried/portapack-mayhem/assets/125336/1415257f-e322-428c-801d-71977603640e)
### Pmem
Displays the contents of the persitent memory area (256 bytes)
It is split into three pages, pages can be changes with the encoder and the current offset from the start of pmem area is displayed on the top "XX+"
At the bottom also the current size of the data_t struct is displayed (this is what we persist into pmem) and the currently stored checksum (it is calculated from the first 252 bytes of the pmem area when changes are made to the settings and then written to the last 4 bytes of pmem)