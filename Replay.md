This app allows users to replay single C16 file, or create playlists of previously captured signals and replay them in a specific order.

The Key Items on the App that can be selected with the cursor and changed with the encoder knob are:

* **Title bar:** The usual Items may be changed and displayed.
* **Open file:** this allows you to select a file form the SD card folders to replay.
* **File Information:** is given next to the “Open file” button giving the file name, length and the speed. Transmission.
* **File progress bar:** To the righthand side of the “Open file” Button is the progress bar this show the progress of the file being transmitted 
* **Frequency:** Which is the first item on the third line below the title bar. This brings up the normal frequency keypad.The information is keep in persistant memory and is avalable from the settings in the Capture App.
* **Gain:** Next in the second line is the LNA (IF) (0-47) and Amp gain A: 0dB or 14dB.
* **Loop:** A tick box that selects that when the file reaches the end of the transmission that it will start the file again. (or entire list if you opened a PPL file)

# Replay Single File

Select a C16 file, it will replay your C16 file referring the freq and rate config of it's partner file.

# Playlist

A sample PLAYLIST.PPL file is included in the SD card.

The file with PPL extension is just text file, you could edit it with any of the text editor.  

Playlist files are comma delimited and have the following structure:

ABSOLUTE_PATH_TO_C16_FILE,DELAY
#COMMENTS

For example, a valid playlist file could contain:
```
# Playlist file example
# capture path, pre-delay milliseconds (optional)
/SAMPLES/TeslaChargePort_US.C16
/SAMPLES/TeslaChargePort_EU_AU.C16,100
```

It will do:  
1. Play SAMPLES/TeslaChargePort_US.C16 referring the freq and rate config of it's partner file 
2. pause 100 ms  
3. Play SAMPLES/TeslaChargePort_EU_AU.C16 referring the freq and rate config of it's partner file  
4. over.  
  
The LOOP check box is for the entire PPL file. 
Once you interrupted the replay, it would start over since the beginning of the list.  

