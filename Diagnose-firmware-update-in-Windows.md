If you cant get firmware to update/install on your device do these steps.

Try boot into DFU mode by:
1. Plug device into computer
2. Press and HOLD the DFU button, While still holding the DFU button, press and release the reset button (WHILE STILL HOLDING THE DFU BUTTON).

> Note : in some particular H2 (ex H2R4 with battery ), reset button does not  make a proper reset , it just freeze the screen , and do not allow you to enter in DFU . In that case,unplug it from the computer, switch off the unit with two sort pushes to the big encoder button (power off). And then keep pressing DFU button , a short push button to the encoder (power on) leads you into a proper DFU Mode. And now you can plug it through USB cable to the computer.


3. Check Windows device manager and see if you have LPC showing up 

![image](https://github.com/eried/portapack-mayhem/assets/4393979/a5d7dccf-ebde-4514-b937-d4e3bd111fa2)

4. If it shows up then make sure you download the latest version of **mayhem_vx.x.x_FIRMWARE.zip** from GitHub here https://github.com/eried/portapack-mayhem/releases/latest. You can then run "dfu_hackrf_one.bat". Now double check the file name as they look quite similar.
5. Once it opens, press enter on your keyboard and you should see the following:

![image](https://github.com/eried/portapack-mayhem/assets/4393979/a1779ad3-b502-4d4b-ba26-4cbec7cd2b76)

6. Once that is done, you need to check device manager and see if you can now see a new device showing up

![image](https://github.com/eried/portapack-mayhem/assets/4393979/419d554c-872c-4c97-81bd-f62cce56fc1d)

7. If this device is showing up, then you can now run "flash_portapack_mayhem.bat" and press enter. You should now see the following:

![image](https://github.com/eried/portapack-mayhem/assets/4393979/c53f0750-e044-49ea-b741-78144519742a)

8. Once that is done, you should be able to press the reset button and your device will boot up. If not, then please refer to the wiki here: [Won't boot](https://github.com/eried/portapack-mayhem/wiki/Won't-boot



### Unknown device
If you see **Unknown device** then you will need to install your device drivers.

![image](https://github.com/eried/portapack-mayhem/assets/4393979/4fe9686f-3769-4469-b532-42ee7acb1554)