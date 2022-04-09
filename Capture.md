Capture App is designed to capture I/Q data. This is  is stored as pairs of 16-bit signed values in a .C16 file (Complex 16 bit) and are stored in little-endian format.The Metadata (“Center frequency” and Bandwidth) is stored in a .TXT file with the same name.In GRC, the "file source" and "ishort to complex" blocks can be used to process the data.

The Sampling rate used may not be supported by some MicroSD cards, it is best to use high speed class SD cards. The HackRF PortaPack Capture/Replay functionality is  based on Havoc firmware version.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Frequency:** The setting of the frequency using the keypad can be completed and is stored in persistant memory so can be returned to when the App is used again.
* **Step Size:** The selected step size of frequency adjustment carried out by the Rotary encoder. 
* **Gain:**  Amp  (0dB or 14dB), LNA(IF) (0-40),VGA(Baseband)(0-62)
* **Rate:** The sample rate, which by its nature set the set bandwidth of capture. This is shown in the markers around the centre line of the waterfall display. The sample rate is variable from 8k5 to 2750K (*)  in 13 steps. You need to ensure that the sample rate is more than twice the bandwidth of the signal  you want to capture see [(Nyquist Principle / also called Shannon’s Law)  ](https://en.wikipedia.org/wiki/Nyquist%E2%80%93Shannon_sampling_theorem)

Note (*)  : Currently , **for correct Replay application ,you should ONLY use Capture App selecting any Bandwith capture <= 600 Khz. (500Khz recommended for majority micro SD cards compatibility)**. 600khz may need fast and good quality micro SD Card , and with not so high random latency . (In the GUI , those correct bandwidth capture options appear with the Normal usual "REC" icon Background colour, as user recomended BW capture options)

Above 600Khz bandwith options (with YELLOW REC button background Icon), in current fw version , the recorded files are “decimated” , and it has not recorded all full original samples content and therefore it is NOT useful for the Replay App , just useful to check the spectrum image, example using the tool "inspectrum" ). Anyway when replaying those captured files , the replay time will be shorter than real . but normally you should always got modulation.
In future versions, it is pending to investigate and try to apply a correct .C16 recording files (without any decimated samples ) till a capture of 1Mhz. 

![image](https://user-images.githubusercontent.com/86470699/162581344-446a1a0b-325e-4bb6-a451-f47ecc91d8e3.png)




* **Record Button:** The red button shows as Rec or Stop. If record is selected then it will record the I/Q file. To the side of the Record Button is additional information that is shown for the recording file. 
  
     * File Name
     * % of the Storge capacity available
     * Total time left 


Please check the video below for HackRF PortaPack Capture/Replay functionality.  [![HackRF PortaPack Capture/Replay functionality](http://img.youtube.com/vi/Pe30Jvyhmzk/0.jpg)](http://www.youtube.com/watch?v=Pe30Jvyhmzk "HackRF PortaPack Capture/Replay functionality")