Capture App is designed to capture I/Q data to a file on the SD card. Captured data is stored as pairs of 16-bit signed values in a .C16 file (complex 16 bit), or optionally 8-bit signed values in a .C8 file (complex 8 bit). C16 values are stored in little-endian format. The Metadata (“Center frequency” and Bandwidth) is stored in a .TXT file with the same name.In GRC, the "file source" and "ishort to complex" blocks can be used to process the data.

The Sampling rate used may not be supported by some MicroSD cards, it is best to use high speed class SD cards. The HackRF PortaPack Capture/Replay functionality is  based on Havoc firmware version.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Frequency:** The setting of the frequency using the keypad can be completed and is stored in persistant memory so can be returned to when the App is used again.
* **Step Size:** The selected step size of frequency adjustment carried out by the Rotary encoder. 
* **Gain:**  Amp  (0dB or 14dB), LNA(IF) (0-40),VGA(Baseband)(0-62)
* **Rate:** The sample rate, which by its nature set the set bandwidth of capture. This is shown in the markers around the centre line of the waterfall display. The sample rate is variable from 12kk5 to 2750K (*)  in 16 steps. You need to ensure that the sample rate is more than twice the bandwidth of the signal  you want to capture see [(Nyquist Principle / also called Shannon’s Law)  ](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem)
* **Format:** The user can select two file formats, of the recorded IQ data 16 / 8 bits :  C16 (complex 16)  or C8 (complex 8), and its related file extension ".C16" or "C8".   (By default we are preselecting C16).

Note (*)  : Currently , **for correct Replay application ,you should ONLY use Capture App selecting any Bandwith capture <= 1Mhz  (but 500Khz recommended for majority micro SD cards compatibility)**. From 600khz till 1Mhz , you may need fast and good quality micro SD Card , and with not so high random latency . (In the GUI , those correct bandwidth capture options appear with the Normal usual "REC" icon Background colour, as user recomended BW capture options)

Above 1Mhz bandwith options (with YELLOW REC button background Icon), in current fw version , the recorded files have periodical sample drops  , and therefore it has not recorded all full original samples content and therefore it is NOT useful for the Replay App , just useful to check the spectrum image, example using the linux tool "inspectrum" or "Audacity") . Anyway when replaying those captured files , the replay time will be shorter than real . but normally you should still get a correct  modulation, but in case of voice contents, it would sound , unnatural , "like with accelerated playing speed" , because in fact,due to Hackrf One System (HW+SW) limitations, those  recorded files (under those high speed BW with YELLOW icon) have decimated its  content - when recorded there were skipped some real time samples. 
In future versions, it is pending to investigate and try to apply a correct .C16 recording files (without any samples drop) till a capture of 2Mhz. (We will keep updated that manual , when we achieve it) 

![image](https://user-images.githubusercontent.com/86470699/162581344-446a1a0b-325e-4bb6-a451-f47ecc91d8e3.png)




* **Record Button:** The red button shows as Rec or Stop. If record is selected then it will record the I/Q file. To the side of the Record Button is additional information that is shown for the recording file. (As we mentioned above, for correct Replay operatons, please make sure to select a proper Capture bandwith option  , with normal black background "REC" icon , not the yellow one.)
  
     * File Name
     * Percentage of Missed Samples (recording error rate, due to SD card write latency)
     * Total recording time remaining (based on available SD card capacity)

Please check the video below for HackRF PortaPack Capture/Replay functionality.

  [![HackRF PortaPack Capture/Replay functionality](http://img.youtube.com/vi/Pe30Jvyhmzk/0.jpg)](http://www.youtube.com/watch?v=Pe30Jvyhmzk "HackRF PortaPack Capture/Replay functionality")