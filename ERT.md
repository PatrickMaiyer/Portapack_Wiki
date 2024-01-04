[Encoder receiver transmitter](https://en.wikipedia.org/wiki/Encoder_receiver_transmitter) (ERT) is a packet radio protocol developed by Itron for automatic meter reading of water, gas and electricity. The system uses OOK short range radio which is transmitted in the unlicensed 902-928 MHz ISM band, so that meters can be read from a passing vehicle. This is mainly used in USA. The data is not encrypted, and does not have functions to enable full control. The system is not as advanced as a smart meter and lacks the control or security in the data transferred. Supported message protocols are IDM, SCM, and SCM+.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Frequency:** The default frequency of 911.6 MHz can be modified in newer firmware (the ISM band is commonly ~902 MHz to 928 MHz).
* **Gain:** Setting are shown in order of AMP 0=0db or 1=14dB, LNA(IF) (0-40) and VGA (Baseband Gain) (0-62).

Fields displays in the App are as follows:

* **ID:** this is the meter ID (in decimal format; should match number/barcode printed on meter).
* **Ty (or Tp):** This is the type of meter as indicated in the message. (Likely meter type codes include Electric: 4, 5, 7, 8, 12;  Gas: 0, 1, 2, 9, 12;  Water: 3, 11, 13)
* **Consumpt:** The Meter reading value.
* **Tamp:** Tamper flags. For SCM type meters the tamper flags are shown as single-digit physical/encoder tamper flags respectively. For SCM+ or IDM type meters the tamper flags are shown as a 4-digit hexadecimal value.
* **Ct (or Cnt):** The count of the number of readings with the same meter ID (or ++ if the field width on the screen is exceeded).

The PortaPack ERT receiver monitors approximately 2.5 MHz centered around 911.6 MHz. It does not implement channel filters, so sensitivity is reduced in exchange for monitoring more simultaneous "channels".

If a FAT-formatted micro SD card is present when this mode is entered, the receiver will log received packets to a file named "ERT.TXT". The log file contains one line per packet received. Each line consists of a timestamp in sortable "YYYYMMDDHHMMSS" format, the Manchester-decoded data bits, a "/", and a per-bit Manchester coding error indicator ("1" if the data bit is in error), and the meter ID.  Received data that looks like it might be a packet (based on the sync bits) but has an invalid checksum will not be listed on the screen although it will be listed in the log file for debug purposes; adjusting the gain values may help in this case.
