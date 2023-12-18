# USB Serial Console

The PortaPack Mayhem firmware exposes a serial console via USB when connected to a Computer.

![291070616-9817bf9d-bd6a-4e8d-b7c9-5074e9965f11](https://github.com/eried/portapack-mayhem/assets/13151053/f00a2a55-0116-4390-b5f4-cb11c4fb262a)

Any serial terminal client can be used to connect like PuTTY, minicom, screen, etc. There are even web based ones (Chrome&Edge, no Firefox): https://www.serialterminal.com/

The terminal exposes the ChibiOS/RT Shell:

![grafik](https://github.com/eried/portapack-mayhem/assets/13151053/0642485a-ff13-4386-a1f4-4516d654d8dc)

# Available Commands
* help
  * lists all available commands.
  * ![grafik](https://github.com/eried/portapack-mayhem/assets/13151053/80e42df3-3db7-4804-bdd7-5e33015781ee)
* info
  * shows the ChibiOS/RT system details.
* systime
  * shows the uptime in ms.
* reboot
  * reboots the PortaPack. This will also work on devices where the reset button is not working.
* dfu
  * reboots the PortaPack into DFU firmware upgrade mode.
* hackrf
  * Starts the original hackrf firmware to use the PortaPack as hackrf.
* sd_over_usb
  * Starts the [SD Over USB](SD-Over-USB) mode.
* flash
  * This is the [Flash Utility](Flash-Utility).
* screenshot
  * Takes a screenshot.
  * ![grafik](https://github.com/eried/portapack-mayhem/assets/13151053/1c5278a9-3977-4bf7-8043-44cc524e8b83)
* write_memory
  * Writes arbitrary memory locations. 
* read_memory
  * Reads arbitrary memory locations. 
* button
  * Simulates a button press.
    * button 1: Right
    * button 2: Left
    * button 3: Down
    * button 4: Up
    * button 5: Select/Enter
    * button 6: DFU
    * button 7: Rotary Left
    * button 8: Rotary Right?
* ls
  * Lists files and directories.
* rm
  * Deletes a file.
* open
  * Opens a file for reading and modification.
    * Note: The current position will be set to the end of the file. Use "seek 0" to move to the start of the file.
* seek
  * Sets the current position inside the currently opened file.
* close
  * Closes the currently opened file.
* read
  * Reads n bytes from the currently opened file.
* write
  * Writes bytes from the currently opened file.
  * ![291070841-9e4ecef9-89bb-4a47-be0c-710384a84a22](https://github.com/eried/portapack-mayhem/assets/13151053/b7156f62-537a-4a7b-9d76-0c197992a040)
