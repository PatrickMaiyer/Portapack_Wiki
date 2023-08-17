The scanner should be able to scan about 20 frequencies per second, as it requires about 50ms to stabilize after re-tuning. 

The scanner will stop on any frequency carrying a signal strong enough. You can adjust the signal threshold with SQUELCH.

For better scanning precision, once a frequency with a powerful enough signal is found, the scanner will analyze it for some extra milliseconds, in order to confirm that the signal is still present (and not a spurious peak).

## Big Numbers Frequency
The big numbers display will show the frequency currently being scanned, using the following color code criteria:

* GREY: Scanning
* YELLOW: Analyzing possible signal
* GREEN: Found a strong enough signal

## Scan vs Search Modes

The scanner can either *Scan* frequencies from a frequency list in memory, or *Search* all frequencies sequentially between a starting and ending frequency range.  The `SRCH`/`SCAN` button toggles between those two operating modes of the scanner app (button indicates the mode that will be switched to when pressed).

## Frequency List

The application loads a list of frequencies (f=) and/or a search range from `FREQMAN\SCANNER.TXT` by default, or you can use the `LOAD` button to load from a different file. You can use the Frequency manager app (Tools -> **Freq manager**) to create or edit frequency list files.

If the application finds a frequency _range_ (a=,b=,s=) in the frequency file, it is loaded into the SEARCH START and END and STEP fields (the Scanner app only supports one search range per file).  Alternatively, you are able to manually input a search range "on the fly" by keying in SEARCH START and END frequencies and the STEP selector.

### Rotary Encoder

Whenever the `<PAUSE>`/`<RESUME>` button is highlighted, the rotary encoder may be used to scroll through the frequencies in the Scan list, or through the Search range (regardless whether *Pause* is active).

## Radio Settings

* **Gain:** Setting are shown in order of **AMP** 0=0db or 1=14dB, **LNA**(IF) (0-40) and **VGA** (Baseband Gain) (0-62).  (These settings are preserved per App if "App Settings" is enabled in Setup)
* **VOL:** Audio volume.
* **SQ:** Squelch level. When *Pause* is not active, the squelch level determines the minimum signal level that will cause the scanner to pause on a strong signal while scanning or searching (until the **Wsa** Wait timer expires). When paused for any reason, the squelch level also determines whether audio output is enabled or *squelched*.
* **MODE:** Modulation mode; **AM** (DSB 9k, DSB 6k, USB+3k, LSB-3k, CW), **NFM** or **WFM**.
* **BW:** Select signal bandwidth (available values depend on modulation **MODE** setting).
* **STEP:** Selects frequency step increment when performing a sequential **SEARCH**.

## Buttons

The purpose of each of the buttons on the screen is as follows:

* `LOAD`: Loads scan frequency lists and/or search ranges from a file (in **Freq Manager** format).
* `MCLR`: Clear list of scan frequencies in the temporary scanning memory (frequencies may subsequently be added to the scan list using `ADD FQ` or `LOAD`).
* `SRCH`/`SCAN`: Switches between Search mode (using the search frequency range) and Scan mode (going through the list of saved frequencies), as described above.
* `<PAUSE>`/`<RESUME`: Manually Pause / Resume the scanning. The **Rotary Encoder** is enabled to manually scroll through frequencies when this button is highlighted.  In SCAN mode, turning the dial will go through the list of saved frequencies.  In SEARCH mode, turning the dial will go through the search range.  When paused or not, the *Squelch* setting may need to be lowered to hear weak signals.
* `FORWARD`/`REVERSE`: Change scanning direction (button shows direction that will be switched to if pressed).
* `MIC TX`: Jump into the MIC TX/RX app (2-WAY Radio)
* `AUDIO`: Jump into the RX->AUDIO app (for further analysis)
* `DEL FQ`: Delete the current frequency on display from the (temporary) scanning memory
* `ADD FQ`: Add the current frequency into the SCANNER.TXT file

## Delay Settings
There are two user-adjustable wait settings while scanning:
* **Wsa:** Wait time while Signal Active, in seconds. When this wait time expires, scanner will skip to the next frequency automatically, even if there is a strong signal present. A value of 0 disables this timer, resulting in the scanner remaining on a strong signal forever, or until changed by the **Rotary Encoder**. A non-zero value of **Wsa** is also known as "Browse" mode.
* **Wsl:** Wait time after Signal Loss, in seconds. When a strong signal drops below the squelch threshold, scanner will remain on this frequency for the specified number of seconds before skipping to the next frequencies.

## Other Fields
When scanning, the current frequency index is shown on the screen, along with the count of number of frequencies in the scan list. If a description is found in a loaded frequency file, the description will also be displayed on the screen above the Big Numbers Frequency (otherwise the loaded file name will appear, or "SEARCHING..." in Search mode).

## Freqman File Format
See [Freqman Manager](Freqman-manager) page

## Example: Using Scanner as a Broadcast FM Radio Tuner
Follow the instructions below to use Scanner as a Broadcast FM Radio Tuner:
1. Press `LOAD`, use dial to select FM_STANDARD_BAND.TXT frequency file, and click Select.  (This will load the Search frequency range, frequency step, mode [WFM], and default bandwidth.)
2. Optionally adjust the Volume (VOL), Squelch (SQ), LNA/VGA/AMP RF gain, and Wsa delay settings.
3. Press `<PAUSE>` to stop the automatic searching.
4. Press arrow keys to move focus to the `<PAUSE>`/`<RESUME>` button.  When the `<PAUSE>`/`<RESUME>` button is highlighted, the manual dial can be used to tune to an FM radio station.
5. Press `ADD FQ` to add the current frequency to the selected frequency file.  Repeat tuning & adding to store additional frequencies.
6. In future listening sessions, just load the same file (step 1) and Scanner will loop through the saved frequencies, spending "Wsa" delay time on each saved station.  To stay on a saved station indefinitely, press `<PAUSE>`.  To manually change stations, move focus to the `<PAUSE>`/`<RESUME>` button and use the tuning dial.  Additional stations may be added in the future by pressing `SRCH`, then `ADD FQ` as desired (step 5).  Consider renaming the frequency file to SCANNER.TXT if you wish it to be loaded automatically whenever the app is started.

## Also see:  Recon app
Advanced users may want to try the [Recon](https://github.com/eried/portapack-mayhem/wiki/Recon) app, which is a more fully-featured Scanner application.

