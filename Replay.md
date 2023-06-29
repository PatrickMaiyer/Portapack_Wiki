This app allows captured signals to be replayed.

# The UI

![Playlist](https://github.com/eried/portapack-mayhem/assets/3761006/8e494c6a-bed6-43f8-8af0-aca58f7958ff)

* The top line is the name of the currently selected capture file to play.
* The second line has the Frequency (which can be modified) and the capure's sample rate.
* At the end of the second line, there are two progress bars. The top indicates the progress in playlist, and the bottom indicates the transmit progress of the current item.
* The third line indicates the length of the current item. You can set the TX gain (0-47), TX amp (0|14), loop mode, and toggle playback.
* The fourth line indicates the current playlist path.

* Left/Right buttons allow you to change the currently selected track.
* + File button will open the file picker to select a new C16 (capture) file to add at the *END* of the playlist.
* X button will delete the currently selected item from the playlist.
* Open button will open the file picker to select a new PPL (playlist) file. This will overwrite the current playlist.
* Save button will save the modification to the current playlist.

- When "Loop" is checked, it will continue to play the entire playlist until stopped.
- Playback always restarts from the beginning of the playlist.
- Once a capture has been added to the playlist, you can modify the playback center frequency. This is done on a per-track basis and is _NOT_ saved as part of the playlist.
- If a capture file is missing its metadata (partner) file, then the TX frequency and 500K sample rate are assumed.
- A new, unique file name is created when a new capture file is added to an empty playlist. This playlist is not saved unless you press save.
- You can also browse to a Capture (C16) or Playlist (PPL) file in the FileMan and select it to open it in Replay.
- NB: Delay (see below) hangs the UI thread and will appear to freeze the device. You have to restart to interrupt the delay.

When the app starts, you have an empty playlist and the "+ File" button is focused. If you just want to play back a single item, press the "+ File" button and select a C16 file.
The play button will be automatically focused once you've made a selection. This allows for fast, 2-click, playback.

# Replay Single File

Select a C16 file, it will replay your C16 file referring the freq and rate config of its partner file.

# Playlist

A sample PLAYLIST.PPL file is included in the SD card.

The file with PPL extension is just text file, you could edit it with any of the text editor.

Playlist files are comma delimited and have the following structure:

```
ABSOLUTE_PATH_TO_C16_FILE,DELAY  
#COMMENTS
```

For example, a valid playlist file could contain:
```
# Playlist file example
# capture path, pre-delay milliseconds (optional)
/SAMPLES/TeslaChargePort_US.C16
/SAMPLES/TeslaChargePort_EU_AU.C16,100
```

It will do:  
1. Play SAMPLES/TeslaChargePort_US.C16 referring the freq and rate config of its partner file 
2. pause 100 ms  
3. Play SAMPLES/TeslaChargePort_EU_AU.C16 referring the freq and rate config of its partner file  
4. over.  

When "Loop" is checked, the playlist will be repeated until stopped.
Once stopped, playback will start over from the beginning of the list.  
