Used to manage files on the SD Card.

## Controls

- Use the encoder or up and down buttons to move between items.
- Use the select (center) key enter a folder or to select an item to take an action on.
- Use the right button to select a folder to take an action on (e.g. rename a folder).
- Use the left button or select the ".." folder to go up a directory.

Selecting a TXT or PPL file will open Notepad so the file can be viewed. Selecting a PNG file will open the Screenshot viewer (this can only view screenshots generated on the device). Use the right button to enter the toolbar for these file types. Exiting Notepad or the Screenshot viewer when launched this way will return back to Fileman.

When viewing a screenshot, press any key to return back to Fileman.

A small, blinking arrow on the right indicates that there are more items if you scroll down.

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

## Known folders
- APRS - holds captures from the APRS app.
- AUDIO - holds captures from the Audio app.
- CAPTURES - holds captures from the Capture app.
- LOGS - holds logs from various apps like Pocsag and Radiosnde.
- SCREENSHOTS - holds screenshots.

## Known Issues
- Only the first 100 items in a directory can be shown.
- Cut/Copy/Paste does not work on folders.
- Folders must be empty in order to be deleted.
- Cut/Copy/Paste does not work with "partner" files.
