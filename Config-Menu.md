The config menu is like a mini BIOS that runs before the firmware is loaded. It currently controls two settings.

* **The config menu does not use the LCD screen.** Do not expect any output there. The config menu does only use the reset and DFU button for input and the TX, RX and USB LEDs for output.

## Entering the Config Menu
You can enter the config menu by pressing reset twice.
* In case of a crash while the firmware is loading the config menu will activate automatically on next boot.
* Some versions of the PortaPack do not have a working reset button. If the device resets when the usb cable is unplugged this can be used to enter the config menu when it's performed twice quickly enough.

When done correctly the TX, RX and USB LEDs will blink fast (8 times per second). At this point press the DFU button once to show the currently active options.

## Available Settings and how to read the blink patterns
* LCD driver (TX LED)
  * Option 1: Automatic detection (TX LED off)
  * Option 2: LCD driver 1 (TX LED on)
  * Option 3: LCD driver 2 (TX LED blinking fast)
  * Option 4: LCD driver 2 QFP100 chip (TX LED blinking slow)
  * Option 5: LCD driver 1 QFP100 chip (TX LED inverse blink slow)

  ```The LCD driver can also be set at power on with the up/down/etc buttons. See [Won't boot](Won't-boot)```

* Disable external TCXO (RX LED)
  * Option 1: external TCXO enabled/autodetect (RX LED off)
  * Option 2: external TCXO disabled (RX LED on)

  ```The "Disable external TCXO" option can also be set in Settings > Radio```

## Switching between modes
Press the DFU button to switch to the next option. 10 presses will return you to the original active option.
* **Don't press the DFU button too fast. Hold it down for at least 200ms or it might be ignored.**
* Once a new option is active it is immediately saved. The device can be restarted and the new selected option will be active.