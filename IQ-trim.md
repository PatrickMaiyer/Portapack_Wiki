IQ Trim allows you to trim "radio silence" from the beginning and end of a C16 or C8 capture file.

![IQTrim](https://github.com/eried/portapack-mayhem/assets/3761006/e83a4ca5-af1d-4aeb-918f-1df056fb3d04)

## UI Components

* **Capture path** - select to pick the capture file to open.
* **IQ Display** - shows the IQ file power in 240 buckets. Green/Red lines indicate the Start/End positions.
* **Start** - Starting sample of the trim region. Can be modified.
* **End** - Ending sample of the trim region. Can be modified.
* **Samples** - Number of samples int the capture file.
* **Max Pwr** - Power (complex magnitude) of the "strongest" samplein the capture file.
* **Cutoff** - Signal to Noise cutoff as a percentage of the Max Pwr. Can be modified.

## Trimming Capture Files
1. Open a capture file. You should hopefully see a trimmable region in the IQ Display control.
   - If you don't see a block in the IQ Display, the capture signal was too weak for the tool.
2. Manually set Start/End or use the Cutoff % to automatically trim.
3. Press "Trim" - the file will be edited. It does not make a backup so be careful with your favorite sample files. Maybe use FileMan to make a backup first.

## Splitting Capture Files
Capture files can be split into multiple files using FileMan and Trim. Use FileMan to make copies of the original capture file, then trim each copy using manually specified Start/End positions.