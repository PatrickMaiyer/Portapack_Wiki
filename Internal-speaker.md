# Pinout

Both versions have a similar layout for the pins you need to use. In the H1, the connector might not be populated and look like this:

[[img/hw_h1_speaker_pinout.png]]

On the H2, normally the connector and cable (use the red and yellow wires, isolate the black one) is included as seen here:

[[img/hw_h2_speaker_pinout.png]]

For both versions, you need a small speaker. Typically a laptop speaker will work, for example: 
https://a.aliexpress.com/_mLuZk4U

Connect `SPK+` and `SPK-` to the speaker and use double sided tape to fix it to the PCB.

Speaker test:
https://www.youtube.com/watch?v=XkaGV9muvbg

## Additional details
A speaker has two wires, `SPK+` and `SPK-`. While there is no sound, the speaker floats on a magnetic field in the middle of its range. When `SPK+` is high the speaker moves forward. When `SPK-` is high the speaker moves backwards. The distance forward and backwards depends entirely on the voltage level.

On the PortaPack, the speaker connector has 3 pins.

`SPK+` is the pin nearest to the edge of the board
`GND` is the connector in the middle, skip it
`SPK-` is towards the centre of the board

### H1 specific setup
On the H1, when you add the new speaker you may find that there is no audio. By default the speaker is disabled.

To enable the speaker:
1. Settings
2. UI Settings
3. Ensure Hide H1 Speaker option is disabled (a red **X**)
4. Click Save

Now a speaker icon will be present on the top line of the display.
If the icon has an **X** it is muted. You can click on it to unmute, it will turn green.

