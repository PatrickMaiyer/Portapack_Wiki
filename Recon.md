# Recon App
![Recon App Menu Entry](https://www.nilorea.net/wp-content/uploads/2022/10/MainScreen.png)

# Introduction
A scan is when using a defined list

A search is when using one or many ranges of frequencies with step. 

The Recon app is full rework of the Scanner app, offering different possibilities and customisations.

Both are using all the frequencies in their hand and pause on a frequency when matching criteria (like modulation, amplitude,...)

The search should be as quick as the scanner, (around 20 frequencies per second)

The search will stop into any frequency carrying a signal strong enough. You can adjust the signal power threshold with the SQUELCH

For better scanning precision, once a frequency with a powerful enough signal is found, the search, like the scanner, will analyze it for some extra milliseconds, in order to confirm that the signal is still present (and not a spurious peak)

You can check some demo videos at https://youtube.com/playlist?list=PL-tahIjVksD3rLlhhtemp6wvddnsYAVzv (warning: some features in the video may have been upgraded since filming)

# Main Screen
![Recon App Main Screen](https://www.nilorea.net/wp-content/uploads/2022/10/MainScreen.png)

Buttons description, from top to bottom, and left to right

* LNA , VGA , AMP , VOL => gains, amplification on/off , volume

* VOL , BW , SQUELCH, W,L => bandwidth for actual demod, squelch is the level of DB to match a signal, wait is the time we will stay on the frequency if it's matching lock_duration*nb_locks. If wait is a negative number, then it represent the time we are staying on a matched frequency waiting for new activity, and a new match during the wait reset the counters. L is the lock wait timer, representing the maximum time we stay on a freq waiting for a lock. The lock wait timer is adjusted to the smallest optimal value at app startup and after a OPT save. You may adjust it if needed.

* Current frequency index / Nb frequencies to search , Current DB value , OPT => the settings page

* Current frequency, RSSI MIN/MED/MAX, Value of timer if current frequency is matching

* START freq, END freq, SEARCH button => set the manual start and end of a range and launch a search on it. These values will be updated by the search if auto update m-ranges is checked. If highlighted, you can use the rotary encoder to adjust start or end

* Mode , step => demod to use and step

* PAUSE , AUDIO , STORE => pause or resume the search. If highlighted, you can use the rotary encoder to manually step in the frequencies/ranges, jump to Audio App, store actual frequency in output file

* FW, RST, MIC TX , REMOVE => forward/reverse , reset search (it's restarting from the beginning of input file), jump to Mic app, remove a frequency from output file

# OPT (Settings)
## Main RECON settings page
![Recon App Main OPT page](https://www.nilorea.net/wp-content/uploads/2022/05/PORTAPACK_SEARCH_APP_SETUP_MAIN.png)

* input file => File from which we will load frequencies or ranges to search (default FREQMAN/RECON.TXT)
* output file => File into which we will save frequency using STORE button or autosave mode (default FREQMAN/RECON_RESULTS.TXT)
* output file name => The name of the current output file. Can be edited when clicking on it so you can set a new filename
* autosave freqs => During the search, matching frequencies will be saved without clicking on STORE. No duplicates will be made
* auto start search => Search will start when entering the app, or when going in and out of OPT
* continuous => If checked then the search will loop when reaching boundaries of the loaded input file or the manual range search
* clear output at start => If checked then the output file is blanked at app start. If you're using that feature and want to keep one of your search results, do not forgot to go into filemanager to rename the file before starting the Recon app one more time

## More OPT settings page
![Recon App More OPT page](https://www.nilorea.net/wp-content/uploads/2022/05/PORTAPACK_SEARCH_APP_SETUP_MORE.png)

One of the first two options have to be checked else nothing will be loaded at all and only manual range search will be available
* input: load freqs  => allow load of frequencies
* input: load ranges => allow load of ranges
* input: load hamradios => allow load of ham radios
* auto update m-ranges => if checked then the manual range start and stop values are updated using the actual searched range values. If it's actually searching a frequency, manual ranges are untouched
* Lock duration => define lock duration in msec for a frequency lock to count 
* Lock number => define number of consecutive locks needed to confirm a matching frequency
* Lock duration => define a single lock duration 
* Number of match => define the numbers of matching (db > squelch) locks to have a freq match
* Match mode => Choose between Continuous and Sparse

# Color features for the wait / lock wait values
* white => okay
* yellow => may experience trouble on some situations 
* red => nearly unusable
* if lock wait is > 2 * (match_duration x nb_match) => white, normal
* if lock wait >=  (match_duration x nb_match) &&  lock wait < (match_duration x nb_match) => yellow may experience trouble on some situations
* if lock wait < (match_duration x nb_match)  => red nearly unusable
* if wait it > 0 it's the time we are staying on a matching freq before skipping => white
* if wait < 0 it's the time we are waiting for new activity before skipping. Any new activity (db>squelch) is resetting the timer to 'abs(wait)' => green
* if wait == 0 it's recon mode. No wait after match. No audio start/stop. Matching freqs are auto saved according to the option in OPT => blue

# Color features for main freq
* white => pause / reading signal
* yellow => got a match, trying to achieve a full lock 
* green => during a search : locked , during a pause: current freq is matching squelch level

# Wait (after lock) modes
* wait > 0 : after a lock stay on freq for 'wait' msecs before skipping to next
* wait == 0 => immediately leave freq after a lock. Use in conjonction of autosave match option to make a quick map of matching frequencies
* wait < 0 : after a lock stay on freq for 'wait' msecs before skipping to next, each new (db>squelch) match reset the counter to 'wait'

# Match counts
Match count is reset to 0 after using one of the following buttons:

* PAUSE 
* FW,RW
* OPT
* SQUELCH

# Matching modes
## Continuous
* measurement is done in lock_duration msecs
* at each lock loop if the mean db is > squelch, it's a match
* it needs nb_match consecutive match to have a lock
* if the lock_duration is too low according to your settings it's going to be coloured yellow / red
* it's quicker because we do not wait lock_duration to get nb_match. It can also miss signals since it's rigorous

## Sparse
* measurement is done in lock_duration msecs
* at each lock loop if the mean db is > squelch, it's a match
* we need nb_match during  before lock_duration expires
* it may take longer: any first match is going to trigger a delay of lock_duration, which wait until it reach 0 or nb_match is reached

# Frequencies to scan
The application parses `FREQMAN\RECON.TXT`  by default. If you set something else in the OPT menu under input, then the specified file will be used
You can use the Frequency manager app (Tools -> **Freq manager**) to add more entries to that list

Alternatively, you are able to manually input a search range "on the fly" by keying in START and END frequencies. It will uses the selected step on screen

If highlighted you can also use the rotary encoder on start / end buttons to adjust the frequency

# Modulation Mode
You can select between **AM** , **NFM** and **WFM** modulation modes

On each modulation you can select bandwidth according to modulation value

Step can also be changed, and is only used in range search (manual or not)

If a custom modulation/bandwidth/step is set on the actual freqman entry (from freqman file), it's used as new defaults for next entries

# Persistant settings 
In the idea to be more user friendly the Recon app is keeping some settings in memory and on the sd card. All the settings that you can set in OPT menus will be saved and restored upon poweroff/on or app restart

Squelch is saved between runs / updates

# Recon file format

As a start just a warning: the freqman GUI have not been improved and may show partial results on new formatted lines

## Description of the fields
`'f=freq' for one frequency `

`'a=start_frequency,b=end_frequency' for a range`

`'r=ham_relay_rx_freq,t=ham_relay_tx_freq' for a HAMRADIO entry`

`m=modulation`

`bw=bandwidth`

`s=step`

`d=description`

**All fields except 'f=' or 'a=,b=' 'r=,t=' are mandatory**. If nothing specified actual value is used, even if actual value is 'not set'

Any application using the original load_freqman_file will only load frequencies, and will try to populate a range in the list instead of manually stepping in. For developers: I've made a new load_freqman_file_ex func which do return an old list format depending on the parameters

The Recon app is using the old as the new format, taking informations when it can

## Freqman Recon file example 

`f=468000000`

`f=468000000,d=Single Freq`

`f=468000000,m=AM,d=Single Freq AM`

`f=468000000,m=NFM,d=Single Freq NFM`

`f=468000000,m=WFM,d=Single Freq WFM`

`f=468000000,m=AM,bw=DSB,d=Single Freq AM DSB`

`f=468000000,m=AM,bw=USB,d=Single Freq AM USB`

`f=468000000,m=AM,bw=LSB,d=Single Freq AM LSB`

`a=87000000,b=110000000`

`a=87000000,b=110000000,m=AM,s=100KHz,d=AM radio search`

`a=87000000,b=110000000,m=AM,bw=DSB,s=250KHz,d=AM radio search LSB`

`a=87000000,b=110000000,m=WFM,bw=16k,s=50KHz,d=WFM radio search s=50KHz`

`r=430150000,t=430550000`

`r=430150000,t=430550000,d=HAM radio`

`r=430150000,t=430550000,m=AM,bw=DSB,d=HAM radio`


## Possible values for modulation/bandwidth

* AM  ( DSB , USB , LSB , CW )
* NFM ( 8k5 , 11k , 16k )
* WFM ( 16k )

## Possible values for Steps

* 5KHz , 6.25KHz , 8.33KHz , 9KHz , 10KHz , 12.5KHz , 15KHz , 25KHz , 50KHz , 100KHz , 250KHz , 500KHz , 1MHz

# Workflow and tips
* When a file is loaded and checkbox 'autostart searching' have been checked, the search is starting as soon as the apps open up, using last launch settings
* If 'autostart searching' is not used, then at the app start the last input list is loaded and the search is set in pause on the first frequency of the list
* To start a search using the input file, use the PAUSE/CONTINUE/RESTART or RST button
* To start a search using the manual entry fields on the main screen, fill START/END and use the SEARCH button
* The rotary encoder can be used on the PAUSE/CONTINUE/RESTART and START/END buttons to adjust the frequencies values
* On a frequency match, if the focus is given to the PAUSE/CONTINUE/RESTART button, press the button or use the rotary encoder to allow you to continue the search. It allows you to go to next matching freq, and trough both direction, changing the search direction on the fly. Pressing the button while in frequency locked mode continue the search using actual direction
* Recon app is doing it's best when using ranges
* Use a low squelch value and step down little by little to start to catch stronger frequencies first. If you're using a too low squelch value then the search will stop on a lot of unwanted but matching criteria frequencies
* Input and output file can be the same files. While it's not advised it can be useful in combination of the input loading options
* Both STORE and autosave will save frequency with current searched frequency or range description, or "ADD FQ" if no description

# Troubleshooting
Most of the time if the Recon app is not working as you expected it's coming from a SDCARD problem. You need a SDCARD for the Recon app to save settings between runs and between settings menu / main gui, and you need a RECON folder at the root of it

If not you will not be able to load a file from FREQMAN directory / save settings

if no frequencies are loading, check that by default the 'input: load X' fields in 'Recon app -> OPT -> More' are all checked. And yes, you HAVE to click save in ordre to save the settings

If by some magic you somewhat trashed the configuration and the app isn't starting anymore, try to delete the RECON/RECON.CFG file using the tools/file manager app

If you're not having your frequencies searched in both direction, maybe you miswrote 'a=' for a single frequency entry

Using the same input and output file is not going to pause a problem until you forgot to uncheck 'clear output at start'. Yeah, you've just clear what you wanted to scan

# Power consumption
A continuous search of 63H41M43S was run by user @vag3d, using the default antenna. Settings were a range from 10MHz to 6MHz, WFM, 5KHz steps, 1s wait

Results: 8002 matching frequencies in the output list, and a consumption as following: 63:41:43 4.8659V 0.4191A 120.448Wh 24.796Ah

The search results were having this form: f=14670000,d=R   10.0000>6000.0000 S  0.0050

