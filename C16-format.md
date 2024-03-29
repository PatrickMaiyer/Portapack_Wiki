The [Capture](https://github.com/eried/portapack-mayhem/wiki/Capture) app records into C16 files, and the Replay app read those files.  _(Support for C8 format has since been added to firmware, but this chapter assumes that files were captured in C16 format; most instructions below apply to C8 files as well by just replacing the 16 with 8.)_

As described in an [issue](https://github.com/sharebrained/portapack-hackrf/issues/139) in PortaPack's repo, this format consist of a tuple of 16 bits signed integers. The first number is I and second Q, forming a complex number. As a result, you get a tridimensional representation of the capture: the real and the imaginary parts in the file (I and Q) versus the time (defined by the sample rate, in this case in an adjacent TXT file with the same filename as the C16).

### Capture Manipulation (Audacity)

You can open the C16 file in Audacity importing it as _Raw data_. Consider the sample rate you used when you did the capture.

<img src="img/c16_import.png" width="400">

It is possible to manipulate the data as if it was audio. When importing the file as signed 16 bit PCM with two channels, the upper channel contains the I and the second Q, as explained above. You can apply filters, add silences, trim, mix and merge.

<img src="img/c16_export_multitrack.png" width="800">

To export the data as a C16 file, select Export, Export Audio ... and then select RAW as a 16 bit signed PCM. After saving, change the extension and you will be able to use the file in the Replay app.

<img src="img/c16_export.png" width="600">

For using the new C16 file in the Replay app, you will also need to include a TXT file with the following metadata (frequency and sample rate):
```
sample_rate=<RATE IN HZ>
center_frequency=<FREQ IN HZ>
```

As a final remark, if you created a new file, be sure that the Project Rate matches your capture:

<img src="img/c16_export2.png" width="300">

### Capture Manipulation (GNU Radio)
 
You can use GNU Radio Companion (GRC) to convert the C16 short into a complex IQ file.  

![c16_GRC_1](https://user-images.githubusercontent.com/18655435/163750552-225a6a62-42dd-4bc3-8b64-f8a718109202.png)

As seen in the image above you'll need to bring in the original C16 file using the GRC block `File Source` setting the output type to short, pipe it to `IShort To Complex`, then `Multiply Consent` using the magic number 1.0 / 32768.0 for the constant, and finally export it with `File Sink`.

The reason that the value 32768.0 is used to normalize the C16 capture is because int16 has a range of -32768 to +32767. 2^15 is 32768.0, so dividing int16 value by 2^15 gives a number that is normalized between -1 and +1.

This GRC script can be found at [`firmware/tools/convert_C16_to_complex.grc`](https://github.com/eried/portapack-mayhem/blob/next/firmware/tools/convert_C16_to_complex.grc)


 
