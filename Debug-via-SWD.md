Coding without the possibility of debugging can be quite time consuming because you are mostly blind. The portapack is an embedded system and requires some work for the comfort.

## Introduction to the Arm Debug Interface (ADI)
 The Arm Debug Interface (ADI) is a specification of both the hardware interface and the logical interface for debugging between a host and one or more devices. Currently, most processors are implementing ADIv5.
The ADI defines a debug access port (DAP), made up of a debug port (DP) and access ports (APs). The DAP is the primary “unit” of the debug interface. A given device will have one debug port, which handles the physical connection with a debugger, as well as a number of access ports that provide access to system resources such as debug registers, trace port registers, a ROM table, or system memory. Thus the DP includes the physical connection (JTAG, SWD) as well as some built-in registers, and each AP has its connections to the system, and a number of its own registers.

![image](https://user-images.githubusercontent.com/86470699/232249222-a22a7124-1e2f-40a7-9569-58b921414f96.png)

![image](https://user-images.githubusercontent.com/86470699/232249414-38c50e17-c031-49bd-b0a4-1bb0c8029b35.png)

 
 ## NXP ARM Cortex-M4/M0 dual-core microcontroller  LPC 43xx Debug Configuration

 Our specific LPC 4330 dual-core microcontroller supports JTAG and Serial Wire Debug (SWD), serial trace, eight breakpoints, and four watch points.


  From  [NXP LPC 43xx product datasheet](https://www.nxp.com/docs/en/data-sheet/LPC4350_30_20_10.pdf)  :

![image](https://user-images.githubusercontent.com/86470699/232248444-d91d9e18-1ea6-4d03-ada8-a7264d659d72.png)

![image](https://user-images.githubusercontent.com/86470699/232248466-be75ee18-f60a-482b-b16b-16cf391c7faf.png)

Following other additional documents from [NXP Community](https://community.nxp.com/pwmxy87654/attachments/pwmxy87654/lpc%40tkb/63/1/LPC_DualCore.pdf)

![3A011E7D-4A5F-4062-9AF7-3244E47C159B](https://user-images.githubusercontent.com/86470699/232255540-69d8e392-f024-48a0-87e0-d04e4c5b3a62.jpeg)


![image](https://user-images.githubusercontent.com/86470699/232252556-9873053d-f03e-4533-b068-8b24c1f723fe.png)

![2A6D5C59-E021-41EB-9565-7212B0A63D1B](https://user-images.githubusercontent.com/86470699/232255570-6380f4c3-6543-4751-85fd-5df0f2f1258e.jpeg)


## Hackrf debugging references
Based on latest [Hackrf User's guide](https://hackrf.readthedocs.io/_/downloads/en/latest/pdf/)
There are various debugger options for the LPC43xx.
It introduces the following ones in chapter 19 (also good source to check),we just attach here the index picture,

![image](https://user-images.githubusercontent.com/86470699/232251597-e0fdf8b4-180d-4077-b6f9-29e6b299392c.png)


Talking about Black Magic Probe , the author mentions , 

"It is possible to attach to the M0 instead of the M4 if you use jtag_scan instead of swdp_scan, but the Black Magic
Probe had some bugs when trying to work with the M0 the last time I tried it."

## What you need
* Black Magic Probe
  * Or something similar. [HackRF](https://hackrf.readthedocs.io/en/latest/LPC43XX_Debugging.html) has a list of hardware that should work. In this example we will be using the [Jeff Probe](https://flirc.tv/products/flirc-jeffprobe?variant=43085036585192) with the portapack H2+ in an aluminium case.

The “Black Magic Probe” or the derivative cost down version “Jeff Probe” are both a combined hardware & software projects. 

(1) At the hardware level, they implement both, **JTAG and SWD interfaces for ARM Cortex A- series and M-series** microcontrollers.

(2) At the software level, they provide a “**gdb- server**” implementation and **Flash programmer** support for ranges of micro- controllers of various brands.

The embedded software of the “Black Magic Probe” and “Jeff Probe” are both an open-source project, and both has its own GitHub project development.

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




## Some notes about unified JTAG / Serial Wire Debug (SWD) interface.
 ARM provides SWJ-DP (serial wire/jtag debug port) via its CoreSight technology which maps SWD pins onto JTAG's clock and reset lines. 
 SWJ-DP therefore **allows using both protocols on the same physical connection** though not necessarily at the same time or with the same programmers as JTAG and SWD would have to be multiplexed in time.



**JTAG requires 4 signal lines**

![image](https://user-images.githubusercontent.com/86470699/232254292-1cc21bfd-a703-4554-bfb3-a9b6d7c6fde5.png)

Following this [Serial Wire Debug (SWD) link ](https://www.allaboutcircuits.com/technical-articles/jtag-implementation-arm-core-devices/)
While the JTAG-DP is a common and familiar example of a debugging interface, most relevant to our discussion is the JTAG alternative defined for Arm devices, the Arm Serial Wire Debug (SWD). **SWD was developed as a two-wire interface** for Arm-core devices with limited pin counts. As microcontrollers tend to be quite dense in peripherals, most Cortex-M devices will implement SWD in place of full JTAG to save pin real-estate. So how does this protocol work? 

SWD is specified in the ADIv5 specification (chapter B4). The TDI and TDO pins from JTAG are replaced by a single bidirectional pin called SWDIO; the test mode select (TMS) pin is removed entirely; and the clock (TCK) remains the same (relabeled CLK or SWCLK). Thus SWD uses only two pins compared to the four pins used in JTAG. To make this work, SWD relies on the repetitive nature of JTAG operations: the state machine is manipulated, data is shifted in or out, and the process repeats. The difference with SWD is there is no state machine. Instead, commands are issued serially over SWDIO, and then that same pin is used for reading or writing data.

There are three phases to SWD communication: packet request, acknowledgment, and data transfer. During packet request, the host platform issues a request to the DP, and this must be followed by an acknowledge response. If the packet request was a data read or data write request, and there was a valid acknowledgement, the system enters the data transfer phase, where data is clocked in (write) or clocked out (read) through SWDIO. After a data transfer, the host is responsible for either starting a packet request, or driving the SWD interface with idle cycles (clocking SWDIO LOW). A parity check is applied to packet requests and data transfer phases. 

The particulars of SWD are best understood by seeing a timing diagram, shown in Figure 2. 

![image](https://user-images.githubusercontent.com/86470699/232254350-5d33790a-42fb-4f1c-bc3f-0e9806b198f1.png)
Figure 2. Timing diagrams showing read and write operations for Serial Wire Debug. 

