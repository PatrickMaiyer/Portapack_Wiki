The signal generator found under Utilities can be used to generate a carrier which can be FM modulated with the following waveforms as defined by the Shape function.
* CW : unmodulated carrier
* Sine signal
* triangle signal 
* sawtooth up signal
* sawtooth down signal 
* square signal
* noise signal

## * Sine / Triangle / Sawtooth up / Sawtooth down / Square
We can select the periodic signal to modulate the carrier , in FM .(and we can adjust below the delta FM deviation) 

![image](https://user-images.githubusercontent.com/86470699/235372191-87eeac6f-e9b1-4cf5-a060-96d1965587a7.png)

![image](https://user-images.githubusercontent.com/86470699/235372207-fe2eb3d1-8171-47ad-8e2d-56f0f1a45d59.png)

![image](https://user-images.githubusercontent.com/86470699/235372227-7bfee042-70aa-46c8-adad-974a879b4ce9.png)

Tone defines the frequency of modulation.

Update when unchecked requires the user to drop carrier, then re-start carrier in order for a change of modulation Shape or Tone frequency to take effect. When checked, values will update on the fly.

Stop after 1s limits carrier duration to 1 second

## * White Noise generator options:
From nightly 1st of May 23 fw onwards, we have added 3 White Noise simulation options.
We are generating simulated White Noise ,using pseudo random noise generator, 8 bits  linear-feedback shift register (LFSR) algorithm, variant Fibonacci.  (Following this wiki [link](https://en.wikipedia.org/wiki/Linear-feedback_shift_register)) 

* noise signal

Those GUI title, is indicating that the contents of the FFT spectrum , has harmonics of n x 20khz,  or n x 10khz, or n x 5khz.
(so user can select the granularity of the noise harmonics, ideally White noise should have all infinite harmonics) .


 Example of the implementation of the first Noise option , n x 20 Khz aprox.

![image](https://user-images.githubusercontent.com/86470699/235372877-9eecb03d-ac05-46d5-be43-858fb8d4d15a.png)


![7E6861D9-77CA-43EA-A67E-10EB8C8AA59F](https://user-images.githubusercontent.com/86470699/236649462-4b835635-a3cb-4f27-aea3-bed659d2d8df.png)


![56259E88-BC41-419F-9BBC-B5C3AF1557F2](https://user-images.githubusercontent.com/86470699/236649465-7fa28ded-d79c-4d4e-9504-05ce04c48a47.png)


Update when unchecked requires the user to drop carrier, then re-start carrier in order for a change of modulation Shape or Tone frequency to take effect. When checked, values will update on the fly.

Stop after 1s limits carrier duration to 1 second

