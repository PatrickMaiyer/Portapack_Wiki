Coding without the possibility of debugging can be quite time consuming because you are mostly blind. The portapack is an embedded system and requires some work for the comfort.

## What you need
* Black Magic Probe
  * Or something similar. [HackRF](https://hackrf.readthedocs.io/en/latest/LPC43XX_Debugging.html) has a list of hardware that should work. In this example we will be using the [Jeff Probe](https://flirc.tv/products/flirc-jeffprobe?variant=43085036585192) with the portapack H2+ in an aluminium case.

![grafik](https://user-images.githubusercontent.com/13151053/225426657-845d777d-f991-43db-9939-9276f3e97c46.png)

* Tools. Lots of tools. I think I used all tools there are:
  * Solder Iron
  * Tweezers
  * Screwdrivers
  * A drill
  * [Vise](https://en.wikipedia.org/wiki/Vise)
  * Multimeter
  * A [file](https://en.wikipedia.org/wiki/File_(tool))
  * Good eyes
  * Steady hands
  * exacto knife
* Your portapack
* [Pin header](https://en.wikipedia.org/wiki/Pin_header) 2x5 1.27mm

![grafik](https://user-images.githubusercontent.com/13151053/225426242-cc3293b7-f4a0-4720-8ab6-f88eb6aad2bb.png)

## The things arrived. What now?
First we need to disassemble the portapack. Lots of screws. You probably already know how to do it. Then locate the debug port LPC_JTAG.

![grafik](https://user-images.githubusercontent.com/13151053/225426435-b9280b9c-c0b1-4fae-a3c5-23a6762be167.png)

> Note: The arrow points to PIN 1. Always ensure that you connect your cable correctly, typically by matching PIN 1 marked on the board to the red stripe on the cable.

You now have two options:
1. Solder the pin header and never be able to close the portapack again.

![grafik](https://user-images.githubusercontent.com/13151053/225426821-15d2f240-1560-4179-a5a9-fd442e16cf5b.png)

2. Solder it to the backside.

![grafik](https://user-images.githubusercontent.com/13151053/225426994-9ecda5d9-8e90-4b1e-a534-3e16a5478b30.png)
![grafik](https://user-images.githubusercontent.com/13151053/225428630-870981a6-6057-4458-a0b0-2522c46ea8b0.png)
![grafik](https://user-images.githubusercontent.com/13151053/225426928-4493d958-9180-4613-a54a-4cc1e8d542dd.png)

## The pins are now backwards. What now?

> Note: Now that the pin header is on the back side it is never possible to correctly connect your cable, because the pins are reversed. Instead of 1,2,3,4,5,6,7,8,9,10 it is now 2,1,4,3,6,5,8,7,10,9.

![grafik](https://user-images.githubusercontent.com/13151053/225427182-de5bbeb5-471f-4809-b87f-060ae5cdc3f4.png)
![grafik](https://user-images.githubusercontent.com/13151053/225427417-07d10ffd-627b-481e-bd21-4e2b99fbafd3.png)

Now we disassemble the ribbon cable to correct the back-'wardity'.

![grafik](https://user-images.githubusercontent.com/13151053/225427596-6ac55f77-0f21-4f3a-81d0-fbda849f46ef.png)
![grafik](https://user-images.githubusercontent.com/13151053/225427684-9e47f519-6f9b-4f6f-a1f6-897ce98d12b5.png)
![grafik](https://user-images.githubusercontent.com/13151053/225427729-18eaa40b-7768-4098-a228-74a4c5f3000d.png)
![grafik](https://user-images.githubusercontent.com/13151053/225427782-bfe6d955-4bd7-4dfa-a50a-4c697f9644e7.png)
![grafik](https://user-images.githubusercontent.com/13151053/225427853-056a0875-fdcb-4018-9550-8ddd166d68c6.png)

Keep pairs of wires together. Insert them back but twist every pair.

![grafik](https://user-images.githubusercontent.com/13151053/225428006-1616377a-e60a-49c1-a84a-5fb2cebf10fb.png)
![grafik](https://user-images.githubusercontent.com/13151053/225428097-8afe5807-d2b5-458f-a0db-ac5ee855bd69.png)

Now press it back together with a vice, but careful.

![grafik](https://user-images.githubusercontent.com/13151053/225428176-a76d2a8d-6f77-42d1-9c2a-11eb0d0de095.png)

Do a [continuity test](https://www.fluke.com/en-us/learn/blog/digital-multimeters/how-to-test-for-continuity) with a multimeter to check if they are all connected. You can use the 'not yet? soldered' pin header to help reach inside. The ends of the wire are easy reachable.

![grafik](https://user-images.githubusercontent.com/13151053/225428353-8a57f90f-d82f-45c8-a3e9-a6b6eb86ee8d.png)

## First test

With the pin header in place and the ribbon cable ready you can run a first test. Attach the hackrf and the battery to the portapack and power on the portapack. The Jeff Probe will also be powered on with some LEDs.

![grafik](https://user-images.githubusercontent.com/13151053/225428821-9b4f3959-aa3d-49f2-a4d7-083b03183abb.png)
![grafik](https://user-images.githubusercontent.com/13151053/225428876-cb671ffd-170e-42c1-9ba0-b40921fe80a0.png)


Now you can put your portapack back together with the exception of the back plate.

![grafik](https://user-images.githubusercontent.com/13151053/225429008-6b794096-c1be-4036-92ba-a5ebf1905a82.png)

## Finishing touch

You now have two options:
1.  Leave the backplate off while you are debugging. The backplate will fit, but you should place something non-conductive like [insulating tape](https://en.wikipedia.org/wiki/Electrical_tape) between the plate and the pins.

2. Make the debug port always accessible by drilling a hole in the backplate.

![grafik](https://user-images.githubusercontent.com/13151053/225429092-bc52512f-d1da-4f7d-96e0-40dc55d9ec62.png)
![grafik](https://user-images.githubusercontent.com/13151053/225429147-f918989c-a00b-4878-b8e6-e21eb6f0de7d.png)

> Congratulation. The value of your portapack has now increased by whatever you spend on tools and hardware and of course by the time you spend ;)

## Use gdb

Now that everything is set up you can connect gdb to the LPC4320.
1.  Start arm-none-eabi-gdb
    * > NOTE: you should now start the ADS-B RX app for this to work
2.  depending on your system connect to the probe by running the command:
    * (gdb) target extended-remote \\.\COM4
      * (on windows check device manager for the right COM port)
    * (gdb) target extended-remote /dev/ttyACM0
      * (on linux dmesg or lsusb will help)
      (example dmesg in linux, when attached Jeff Probe to the USB)

       ![image](https://user-images.githubusercontent.com/86470699/232033188-ab87601f-2030-47dd-b075-5aca0258480f.png)


3.  now check the fw version of the probe
    * (gdb) monitor version
    (example of Jeff Probe answer)

      ![image](https://user-images.githubusercontent.com/86470699/232032197-1fa0d819-4c88-47df-b47b-431213291029.png)

4.  scan for devices
    * (gdb) monitor swdp_scan
5.  attach to the device
    * (gdb) attach 1
6.  load the symbols
    * (gdb) file firmware/baseband/baseband_adsbrx.elf
7.  look around
    * (gdb) info threads
    * (gdb) info registers
    * (gdb) tui enable
    * (gdb) continue

## Limitations and Issues
* M0 seems inaccessible
* VSCode integration is rather buggy
* When you stop debugging you have to power down your jeff probe for it to work again.

## Integration into VSCode
> NOTE: Using WSL on Windows has some issues forwarding the usb device to the linux host. I used vscode on Windows with 'Remote - SSH' extension to an old laptop running ubuntu where i could attach the jeff probe directly.

First create your .vscode/launch.json

```json
{
    "version": "0.2.0",
    "configurations": [
    {
        "name": "(gdb) JTAG probe",
        "type": "cppdbg",
        "request": "launch",
        "miDebuggerPath": "arm-none-eabi-gdb",
        "targetArchitecture": "arm",
        "program": "${workspaceRoot}/build/firmware/baseband/baseband_adsbrx.elf",
        "cwd": "${workspaceRoot}",
        "setupCommands": [
            // use logging for troubleshooting
            //{"text": "set logging file ${workspaceRoot}/build/arm-none-eabi-gdb.log"},
            //{"text": "set logging on"},
            {"text": "file '${workspaceRoot}/build/firmware/baseband/baseband_adsbrx.elf'"},
            {"text": "target extended-remote /dev/ttyACM0"},
            {"text": "monitor swdp_scan"},
            {"text": "attach 1"},
        ],
        "launchCompleteCommand": "None",
        "externalConsole": false,
    }
    ]
}
```

Setting breakpoints and attaching without breakpoints does not work very well. So we have to do it by hand. In code.

Add this macro somewhere in firmware/baseband/proc_adsbrx.cpp
```c
#define HALT_IF_DEBUGGING()                              \
  do {                                                   \
    if ((*(volatile uint32_t *)0xE000EDF0) & (1 << 0)) { \
      __asm("bkpt 1");                                   \
    }                                                    \
} while (0)
```

And call it inside a loop.

![grafik](https://user-images.githubusercontent.com/13151053/225966194-53c3eb3f-f00f-458d-ba6f-0874165aba69.png)

Now:
* make firmware
* flash firmware to portapack
* start the ADS-B RX app
* attach the jeff probe to usb and portapack
* start the debugging profile

![grafik](https://user-images.githubusercontent.com/13151053/225966101-1b838b97-f845-40e2-b02e-44d9ecbb5770.png)

It should stop at the breakpoint now. Press F10 to step through the code.