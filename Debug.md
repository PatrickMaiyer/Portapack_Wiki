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



## Temperature 
Data is provided by the MAX 2837 on chip digital temperature sensor. The accuracy is quoted as 4.33°C per value.
## Buttons Test
This shows when either the buttons are pressed, the encode knob is turned or the screen is touched. It can also show if the encoder when turned is cleanly stepping the states as it is turned. Note on cheep portapack clones of the encode that is 24 step version can be over sensitive and miss steps. It can be changed with a better-quality version.

![SCR_0013](https://github.com/eried/portapack-mayhem/assets/125336/1415257f-e322-428c-801d-71977603640e)
### Pmem
Displays the contents of the persitent memory area. (256 bytes)

It is split into three pages, pages can be changes with the encoder and the current offset from the start of p.mem area is displayed on the top: "XX+" Also on the last page theres some padding with FFs displayed after the p.mem area ends.

At the bottom it displays also the current size of the data_t struct (this is what we persist into p.mem) and the currently stored checksum (it is calculated from the first 252 bytes of the p.mem area when changes are made to the settings and then written to the last 4 bytes of p.mem)

The version of the stored config isnt displayed separately but it can be seen as the first 4 bytes of the p.mem area.