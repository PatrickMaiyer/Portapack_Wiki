This app allows users to create playlists of previously captured signals and replay them in a specific order.  

A sample PLAYLIST.PPL file is included in the SD card.

The file with PPL extension is just text file, you could edit it with any of the text editor.  

Playlist files are comma delimited and have the following structure:

FREQ,File_PATH,SAMPLE_RATE,PULSE_TIME   
The unit/dimension of PULSE is `ms`, and it's for to give a pulse/delay before the C16 file which is at same line, were played.

For example, a valid playlist file could contain:
```
315000000,SAMPLES/TeslaChargePort_US.C16,500000,0
433920000,SAMPLES/TeslaChargePort_EU_AU.C16,500000,50
```


It will do:  
1. Play SAMPLES/TeslaChargePort_US.C16 at 315000000 Hz freq, with 500000 rate  
2. pulse 50 ms  
3. Play SAMPLES/TeslaChargePort_EU_AU.C16 at 433920000 Hz freq, with 500000 rate  
4. over.  
  
The LOOP check box is for the entire PPL file. 
Once you interrupted the replay, it would start over since the beginning of the list.  

We apologize that we changed the grammar of PPL probably several times, even though we did some compatibility work, for example you actually don't need to specify the delay/pulse timing if you don't need that, still, pls try to use the standard grammar, because it would be hard to take care of all the possible case in limited  code in a very old CPLD. And limited storage.    

[Video demonstration of playlist app](https://user-images.githubusercontent.com/164560/191515258-36621648-3827-4eed-b77b-e8dbaf9be63e.mov)

https://github.com/eried/portapack-mayhem/assets/24917424/fee71d13-855a-4955-ad6d-6ae21d24970a



