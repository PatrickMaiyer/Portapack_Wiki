The Microphone App provided till firmware version 1.3.1  a Narrow band  FM  transmitter application, that allows the transmission of voice and when not transmitting allows you to receive in a simplex way if configured. 

From firmware version 1.4.0 onwards,  it has been added some other additional analogue  mod(TX) /demod (RX)   FM/AM/LSB/USB/DSB.  

## Key Controls

* **MIC. GAIN:** Cursor selection and use rotary encoder is used to select a fixed gain of x0.5, x1.0, x1.5, x2.0. The setting needs to be selected based, on the Microphone used which is connected via the Headset/ Microphone socket (standard smartphone 4 segment 3.5mm connector). The sensitivity of the microphone is shown in a vu-meter on the lefthand side and should be configured so the range is green for most of the audio and never hits red to limit over deviation of the signal. (see annexed image) 
Note : this mic GAIN , is scaling the captured audio samples, therefore it will help to adjust properly the modulation index ,when we have a correct audio mic input. But if we are already saturating the ADC inputs (talking too close to the mic) , it will not help us so much to reduce that ADC input distortion , because the scaling is post ADC stage) .  

![image](https://user-images.githubusercontent.com/86470699/167274133-375621ba-f615-427f-8121-2353a3095069.png)



* **F:** This field set the TX Frequency for the transmission.	

* **BW:** This field sets the +/- FM Frequency deviation (adjustment range 0-150 Khz) . 
(WFM systems usually +/-75 Khz,  NFM :  a typical VHF/UHF two-way radio signal is using 5 kHz peak deviation)
That parameter , is directly related to the transmitted FM channel spectrum (see Carson's bandwidth rule)

* **GAIN & AMP :** Is set for TX_GAIN (IF) and (0-47) and TX RF AMP 0dB or 14dB.Node transmission gain , to all modulation systems from fw version 1.4.0 onwards ,  FM/AM/LSB/USB/DSB)

* **MODE :**  Selection TX modulation type (FM/AM/USB/LSB/DSB) 

(You can see different screens , when selecting different modulation modes. To avoid user confusions,the non available options are hidden )
![image](https://user-images.githubusercontent.com/86470699/167274656-e7eb95a3-ef4a-4820-8f75-2f51413a7406.png)




* **TX Activation:**    Field can be selected for one of three settings. Off, PTT, AUTO. In the PTT setting, the PortaPack will transmit when the TX button and the bottom of the App screen is pressed on the touch screen.  In AUTO the Receiver section below is not active, but the triggering is set by the following 3 settings.

* **LVL:**  The level that triggers the transmission is set by the audio level going over the threshold value set (0-255). This can be seen as a grey dash marked next to the vu-meter and shows its current setting compared to the microphone level.

* **ATT:** This is the attack time of the microphone audio level must be above the set threshold to start transmitting (0 to 999mS). Higher attack helps avoid false triggers but might cut off the first words you say.

* **DEC:** This is the decay time of the microphone audio signal falls below the threshold level be for the transmission is stopped (0 to 9999mS). Lower decay avoids silence at the end of the message but might cut you off in the middle of a sentence. Adjust levels depending on your speaking habits.

* **TONE KEY & CTCSS (only available in FM mode) :** The Tick box next to “Roger Beep” can be selected with effort with cursor or better to select with touch screen.  This is offering to the user , the ability to add to the mic voice , a single continuous specific frequency sine tone , that could be a subcarrier above or below used-audio-bandwidth to activate ham repeaters (example)  , or just add it as CTCSS (Continuous Tone-Coded Squelch System) 
Note the level % of the Tone compared to the Microphone,  can be set in the menu ,  Settings >Audio.  

![image](https://user-images.githubusercontent.com/86470699/167274573-14fcc124-5a0d-4dff-94a5-11e2c62b583c.png)


* **ROGER BEEP (currently only available for FM / AM / DSB)  :** This will add a roger beep if enabled.

* **RX audio listening:** The Tick box to select this item is difficult to select with cursor having to go down and up though item, and with some luck you may enable the box. It is better to select from the touch screen. If this is enabled then it will turn on the Audio Receiver and with the following setting will allow you to listen to a receive channel when not transmitting. The TX-RX timing gap is not known. The frequency can be set separately to that of the transmitter section above. The following setting can be applied to the receiver.
(Note the demodulation type , is linked automatically to the TX Mode type :  FM/AM/USB/LSB/DSB) 

* **FM RX BW (this option is only applicable and available to the FM reception) :** The is the narrow band FM Receiver Band Width setting. It can be set to either 8k5kHz,11Khz or 16kHz. 

* **F:** The RX frequency can be set in the usual way with text pad when selected

* **SQ:**  This can be set between 0 and 99 typically 50 is threshold.

* **GAIN:** The RXgain setting of LNA(IF) (0-40) VGA(Baseband)(0-62) and AMP 0=0db or 1=14dB.

Note this application while performing a transmit function  may well over deviate and generate unwanted harmonics.