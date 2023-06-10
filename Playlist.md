This app allows users to create playlists of previously captured signals and replay them in a specific order.  

A sample PLAYLIST.PPL file is included in the SD card.

The file with PPL extension is just text file, you could edit it with any of the text editor.  

Playlist files are comma delimited and have the following structure:

FREQ,File_PATH,SAMPLE_RATE,PULSE_TIME 
The unit of PULSE is `ms`, and it's for the pulse before the file at same line.

For example, a valid playlist file could contain:
```
315000000,SAMPLES/TeslaChargePort_US.C16,500000,0
433920000,SAMPLES/TeslaChargePort_EU_AU.C16,500000,50
```

It will do:  
Play SAMPLES/TeslaChargePort_US.C16 at 315000000 Hz freq, with 500000 rate  
pulse 50 ms  
Play SAMPLES/TeslaChargePort_EU_AU.C16 at 433920000 Hz freq, with 500000 rate  
over.  
  
The LOOP check box is for entire PPL file. 

[Video demonstration of playlist app](https://user-images.githubusercontent.com/164560/191515258-36621648-3827-4eed-b77b-e8dbaf9be63e.mov)

https://github.com/eried/portapack-mayhem/assets/24917424/fee71d13-855a-4955-ad6d-6ae21d24970a



