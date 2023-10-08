Used to manage files on the SD Card.

## Controls

- Use the encoder or up and down buttons to move between items.
- Use the select (center) key enter a folder or to select an item to take an action on.
- Use the right button to select a folder to take an action on (e.g. rename a folder).
- Use the left button or select the ".." folder to go up a directory.

A small, blinking arrow on the right indicates that there are more items if you scroll down.

### File type handlers
Selecting certain types of files launch a viewer for the content. Use the right button to enter the toolbar for these file types. Exiting  the viewer when launched this way will return back to Fileman.
- BMP files will open in the Splash viewer. If the file is of the correct size and type, it can be set as the splash screen.
- TXT files will open in Notepad
- PPL and C8 and C16 files will open in Replay in the correct mode.
- PNG file will open the Screenshot viewer (this can only view screenshots generated on the device). When viewing a screenshot, press any key to return back to Fileman.

## Buttons

![Tools_File manager](https://github.com/eried/portapack-mayhem/assets/3761006/9a138517-c66b-4a4f-8456-b48b84f9ec85)

When an item has been selected, the following commands are available in the toolbar.
- Rename - rename the file or folder.
- Delete - delete the file or folder.
- Cut - add the selected item to the clipboard to be moved.
- Copy - add the selected item to the clipboard to be copied.
- Paste - move/copy the content of the clipboard into the current folder.
- New Dir - create a new folder in the current folder.
- New File - create an empty file in the current folder.
- Open in Notepad - (not shown) open the file in the text editor.
- Exit - exit the file manager.

## Partner files
- Capture files (.C16) will have a "partner" .TXT file containing metadata. Renaming or deleting one of the pair will prompt the same action to be applied to the other.

## Known folders include
- ADSB - holds map and airline data for the ADSB RX app.
- AIS - holds data for the AIS app.
- APRS - holds captures from the APRS app.
- AUDIO - holds captures from the Audio app.
- CAPTURES - holds captures from the Capture app.
- DEBUG - holds debug dump files created from the Debug Dump app.
- FIRMWARE - recommended directory to store alternate Mayhem firmware images.
- FREQMAN - holds frequency list files for the Freqman, Scanner, Recon, and Looking Glass apps.
- GPS - holds data for the GPS Sim app.
- LOGS - holds logs from various apps like ADSB-RX, ERT, TPMS, Pocsag and Radiosnde.
- LOOKING GLASS - holds preset frequency ranges for Looking Glass app.
- PLAYLIST - holds play list files for the Playlist app.
- SCREENSHOTS - holds screenshots.
- SETTINGS - holds saved App Settings.
- SPLASH - (You can create  that folder to store all your favorite splash.bmp files ,and you can just navigate with FileMan 
            and when you open any picture , it will be overlay an Os Screen Display  message on top , with indications
            about how to select it as your next boot default splash.bmp) 

   ![image](https://github.com/eried/portapack-mayhem/assets/86470699/bf09723e-3922-4b76-8d6f-f950f76f8b05) 
   ![image](https://github.com/eried/portapack-mayhem/assets/86470699/15320f59-f8fb-4dcc-89f9-9b3faac50870)


## Known Issues
- Only the first 100 items in a directory can be shown.
- Cut/Copy/Paste does not work on folders.
- Folders must be empty in order to be deleted.
- Cut/Copy/Paste does not work with "partner" files.

