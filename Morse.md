The Morse App sends Morse coded message either in CW or FM. There are some pre-configured foxhunt messages , but these are not useful as  in most countries a callsign must be part of the message, or sent at regular intervals.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Foxhunt:** This tick box enables  the pre-set messages strings ( 11 of them)  that are selected on the same line  such as  “3 (MOS)”.
* **Speed:** Select the speed of transmission in Words Per Minute. (10-45). Note the label should be “wpm” not “wps”, this is a bug.
* **Tone:** This sets the tone for the FM transmission (0-9999).
* **Modulation:** This is set to CW or FM.
* **Loop:** this set the looping of the message and has a value of “Off” or 6 time settings from 5 Second to 5 Minutes.
* **Set message:** When selected, this  brings up the a text keypad and enables the construction of a message.
* **Frequency:** At the lower part of the App is the Frequency setting. This is stored in persistent memory. 
* **Step size:** This is next to the frequency and allows the selection of the standard step sizes.
* **Deviation:** This is located next to the Step size  and allows the setting  of deviation from 1 kHz to 150kHz.
* **Gain:** The gain setting are below the frequency and marked (0-47) LNA(IF) and AMP 0=0db or 1=14dB.
* **Transmission Progress bar:** This bar indicated the progress of the transmission. Above it is shown the transmission time based on the message length.
* **Start:** This button starts the transmission and if pressed again can stop the transmission.

# Important note
Due to the way it is designed, the first 2 characters are somewhat not sent. If you encounter the problem, try prefixing your message with two characters, like 'E' and space. Example: "E MyMessageStartsHere"  (see issue [!303](https://github.com/eried/portapack-mayhem/issues/303) if you think you can help)

