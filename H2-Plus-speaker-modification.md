The H2+ Version R2, R3 and R4 uses an WM8731 Codec and supports a speaker using a dedicated Audio Amplifier INS8002e. This is a 3-watt amplifier and should give a high volume.

The issue is that when the volume is at 50 (Default) it gives a good safe volume level in the headphones, but the speaker audio is unable to be heard unless you turn up the volume to 80+ on the volume setting and even then, the audio is low.

Having traced the circuit on the PCB, and studied the chip specifications for the WM8731 and INS8002e, there is an error in the selected component, for the INS8002 gain setting of what is a Power Op-Amp.

The power audio amp input is taken from “Right Channel” headphone connection on the speaker side of the of the headphone socket switch and is connected to the audio amp via a capacitor and 4k7 resistor. The feedback resistor from the output to the input is also 4k7 resistor. This sets the gain for the audio amp at 1. This is totally inadequate.

In tests the feedback resistor can be changed to 47K. This gives a gain of 10 and provided a reasonable safe audio speaker level when the speaker is selected at the default value.

The replacement of the resistor is not easy, and then you need the skills and tools to remove and replace it. The current resistor is SMD 0402 being just 1.0mm long and 0.5mm wide, The indicated resistor should be remove with soldering iron solder pads cleaned and fluxed, and the new resistor added. A larger SMD could be used if soldered to one pad and small wire connected from the other pad to the other end of the SMD.

![Spearker Mod Resistor](https://user-images.githubusercontent.com/32274981/164781350-6f921fdd-5bfa-479f-8f2f-b3f520ee4c6e.jpg)


In the H2+ R4 version the headphone jack switch is disabled. When a pair of headphones are plugged in the internal speaker is not disconnected.

A simple but delicate modification can enable the headphone switch functionality by placing some Kapton tape over the PCB PAD and soldering a small wire from the headphone jack connector to the capacitor into the speaker amplifier.

After the modification when a pair of headphones is plugged in the internal speaker is silenced.

In the first image red traces are for the left channel and blue for the right channel.
1. Remove the headphone jack and clean the pads.
2. Cut the blue trace between the PCB VIA (green dot) and capacitor to the amplifier. Be careful of the other traces.
3. Place a small piece of Kapton tape over the the PAD (top right in the photos).
4. Solder the headphone jack back in place.
5. Solder a short wire from the headphone jack pin to the capacitor (glue the wire to the PCB to avoid it damaging the pin or capacitor).

![PortaPack audio mod](https://user-images.githubusercontent.com/54041511/195446597-310e0379-72b1-4f38-9260-16add6a3c15f.png)

![PortaPack Audio Mod finished](https://user-images.githubusercontent.com/54041511/195446633-6ba257b9-45d3-4bfc-a2c0-edc31a0f8091.png)
