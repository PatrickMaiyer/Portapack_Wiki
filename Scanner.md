The scanner should be able to scan about 20 frequencies per second, as it requires about 50ms to stabilize after re-tuning. 

The scanner will stop into any frequency carrying a signal strong enough. You can adjust the signal power threshold with the SQUELCH.

For better scanning precision, once a frequency with a powerful enough signal is found, the scanner will analyze it for some extra milliseconds, in order to confirm that the signal is still present (and not a spurious peak).

## Big Numbers Frequency
The big numbers display will show the frequency value currently being scanned, using the following color code criteria:

* GREY scanning
* YELLOW analyzing possible signal
* GREEN found a strong enough signal


### Frequencies to scan

The application parses `FREQMAN\SCANNER.TXT`  by default. You can use the Frequency manager app (Tools -> **Freq managern**) to add more entries to that list. 

Alternatively, you are able to manually input a scanning range "on the fly" by keying in START and END frequencies, while adjusting the STEP selector. 

### Modulation Mode
You can select between **AM** (DSB 9k, DSB 6k, USB+3k, LSB-3k, CW), **NFM** and **WFM** modulation modes.

## Bottom Buttons

There are six buttons at the bottom of the screen, useful for the following tasks:

* Manually Pause / Resume the scanning
* Change scanning direction
* Jump into the MIC TX RX app (2-WAY Radio)
* Jump into the RX->AUDIO app (for further analysis)
* Delete the current frequency on display from the (temporary) scanning memory
* Add the current frequency into the SCANNER.TXT file