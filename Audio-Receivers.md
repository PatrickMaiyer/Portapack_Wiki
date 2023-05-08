The Audio App is the main way that signals can be heard and seen in detail. Three types of decoders are provided for audio modulated signals and a spectrum view of the signals. The user interface has the ability to view and change:
 

* **SPEC:** Display a Spectrum of the received signal and allow viewing of 10MHz of RF Spectrum, centered on a configurable frequency, with 5MHz above the frequency and 5MHz below.

* **AM:** Demodulate and Record RF Signals modulated using the Amplitude Modulation scheme. It can demodulate Double-Sideband AM (ITU Designation: A3E) and both Lower-Sideband and Upper-Sideband Single-Sideband AM (ITU Classification: R2E, H3E, J3E) signals.

* **NFM:** The Narrow Band Frequency Modulation decoding ITU Classification: FM3

* **WFM:** The Wide FM Receiver is a Sub-Application of the Audio Receiver Application. Its purpose is to Demodulate and Record RF Signals modulated using the Frequency Modulation scheme. It can demodulate mono and stereo Wide FM signals of 200KHz bandwidth. Such signals are commonly used for VHF FM Broadcast services.

The Key Items on the App that can be seen or selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.

* **Mode:** On the line below title bar is the demodulation mode AM, NFM, WFM, SPEC. When either of these are selected it will bring up a secondary set of relevant items on the line below. These are discussed in secondary items below.

* **Frequency:** The Centre frequency of the demodulation band. 
  
* **Gain:** Settings are shown in order of LNA(IF) (0-40) and VGA (Baseband Gain) (0-62). When either of these are selected in the secondary line the AMP setting is shown and can be as either set to  0=0db or 1=14dB.

* **Signal Display:** The three coloured displays are top to bottom RSSI(Red/Blue) with an average marker in the line. Next is the Baseband signal and last the Audio level.

* **Volume:** The Last item on this line is the audio volume control (O-99) that is used with either headphone or speaker if fitted.

* **Secondary Information:** This line provides associated information for the following items these are:

    * **AM:** Bandwidth settings of DSB 9k, DSB 6k, USB+3k, LSB-3k, CW. The Spectrum view is +/-20k.
    * **NFM:** Bandwidth Settings of 16k,11k,8k5. Note there is no setting for the more common 6k5 used in European Spectrum plans. Next item is SQ: which is shown in the format of 40/99 allow the noise squelch point to be set Between 0-99. Typically, around 40-50 is a good threshold.
    * **Gain:** The RF Amp settings. The Spectrum view is +/-20k.
    * **WFM:** There are three option filters in that Secondary settings : 

     * (1) 200k ,the original filter for commercial FM stations with soft transition, 

     * (2) 180k with sharp transition, for also commercial FM broadcast station, specially useful to improve demodulated S/N in around 6 to 8 dB‘s in weak signals . 

     * (3) 40k with also sharp transition, for supporting NOAA APT weather satellite reception in 137 MHz . (that filter is too narrow for WFM with 75khz delta deviation and can produce audio distortion in the demodulated sound). The Spectrum view is +/-100k with a marker That may be changed (though seem the incorrect value).

    * **SPEC.** The spectrum Secondary Items allows the view of the RF spectrum with different setting for maximum bandwidth shown:
            
            20M with markers at +/- 5M
            10M with markers at +/- 3M
            5M with markers at +/- 2M
            2M with markers at +/- 500k
            1M with markers at +/- 300k
            500k with markers at +/-200k

The next item is the setting of the bin sizes used for the waterfall (0-63) with “0” being the minimum information being the fastest display and “63” the maximum information collected the slowest display. Adjust to give a balance of speed and information seen. 

* **CTCSS:** This Continuous Tone Coded Squelch System is a display at the end of the secondary information line. It is used by many systems and standardised by EIA/TIA, with a description [here.](https://en.wikipedia.org/wiki/Continuous_Tone-Coded_Squelch_System ) The display of the CTCSS shows the tone decoded as a Number and Letter code not the actual tone code itself. See the Annex to this document below. It should be noted that most of the time the display is jumping around and only clearly displays the received tone when there is a gap in the voice and the Signal is of good quality. 

* **Record:** The record button if selected will show the record file name, % of the SD Card used, and at the end of the line is the total recording time available left on the SD card and this decrements when recording. 

## CTCSS Tone List

	None      0.0 
	0 XZ      67.000 
	1 WZ      69.400 
	2 XA      71.900 
	3 WA      74.400 
	4 XB      77.000 
	5 WB      79.700 
	6 YZ      82.500 
	7 YA      85.400 
	8 YB      88.500 
	9 ZZ      91.500 
	10 ZA      94.800 
	11 1ZB      97.400 
	12 21Z      100.000 
	13 1A      103.500 
	14 1B      107.200 
	15 2Z      110.900 
	16 2Z      114.800 
	17 2B      118.800 
	18 3Z      123.000 
	19 3A      127.300 
	20 3B      131.800 
	21 4Z      136.500 
	22 4A      141.300 
	23 4B      146.200 
	24 5Z      151.400 
	25 5A      156.700 
	40 --      159.800 
	26 5B      162.200 
	41 --      165.500 
	27 6Z      167.900 
	42 --      171.300 
	28 6A      173.800 
	43 --      177.300 
	29 6B      179.900 
	44 --      183.500 
	30 7Z      186.200 
	45 --      189.900 
	31 7A      192.800 
	46 --      196.600 
	47 --      199.500 
	32 M1      203.500 
	48 8Z      206.500 
	33 M2      210.700 
	34 M3      218.100 
	35 M4      225.700 
	49 9Z      229.100 
	36 --      233.600 
	37 --      241.800 
	38 --      250.300 
	50 0Z      254.100 
	Axient 28kHz      28000.0 
	Senn. 32.768k      32768.0 
	Senn. 32.000k      32000.0 
	Sony 32.382k      32382.0 
	Shure 19kHz      19000.0 
