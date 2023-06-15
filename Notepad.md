Views text files and supports very basic editing.

## The interface

<img width="240" alt="Notepad" src="https://github.com/eried/portapack-mayhem/assets/21130052/f7591165-9965-441f-b8cf-1e4f2dc04566">

The menu button on the bottom right opens and closes the main menu. On start, this button will immediately show the file picker.

The file can be navigated with the direction buttons. Additionally, the encoder can be used to scroll. The encoder direction is set by the last direction button that was pressed. If you want scroll horizontally, first press the left or right button. When scrolling vertically, the encoder moves 16 lines per step in order to make scrolling through large files easier.

The center (select) button will show the main menu. To close the menu again, click the menu button on the bottom right.

## Opening a file

There are two ways to open a file. If you first open Notepad, select the menu button and the file picker will be displayed. You can also open a file from within Fileman by selecting a file and clicking the Notepad icon in the toolbar.

## Editing a file.

The following edit modes have been implemented.
- Delete line (- Line) - deletes the line the cursor is on.
- Add line (+ Line) - adds a new line above the line the cursor is on. If the cursor is at the very end of the file, adds the newline below the cursor.
- Edit - opens the [text entry](Text-Entry) view to edit the current line. If the line is very long, this may crash due to memory constraints. Using "back" will cancel the edit. Selecting "Ok" will commit the edit to the file.

## Known limitations

- Exiting Notepad with the "back" button (top left) will _not_ prompt you to save. Your changes are not lost. Any in-progress edits are saved in the temp file "filename.ext~". You can recover this file using "Rename" in Fileman.
- Edits on larger files are slow. It currently requires multiple passes over the file contents because all operations are performed directly on the file contents (vs. in-memory) in order to work within the memory constraints of the device.
- The first edit is additionally slow because it copies the source file on first write. This is to allow changes to be made that can be discarded.
- There's currently no UI indication that the program is performing IO. As long as you don't see a fault, it should be working. Just be patient.
- Cut/Copy/Paste is not implemented yet.
- The cursor doesn't automatically get updated after edits. Navigation will snap the cursor back to the text.