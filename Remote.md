The remote app allows you to create a custom remote UI and bind buttons to captures.

![RemoteUI](https://github.com/eried/portapack-mayhem/assets/3761006/b0c2245b-d7bd-480e-973a-77b062ac6bfc)
![RemoteEdit](https://github.com/eried/portapack-mayhem/assets/3761006/86783dbe-c51a-44ab-942b-743b9cb3c4c8)

## Main UI

* **Remote Title** - The top line is the title of the remote. Select it to edit it.
* **Remote Buttons** - Up to 12 customizable buttons per remote. Select a button to transmit the capture file. Press again to stop. Long-press select to edit or delete the button.
* **Waterfall** - A small waterfall is shown while transmitting below the button grid.
* **Gain** - Control the transmitter Gain and Amp. The color indicates the overall transmitter power.
* **Loop** - Continuously transmit until stopped.
* **Filename** - Shows remote file name. Select it to rename the remote file.
* **Add Button** - Add a new button to the grid. New buttons will open in edit mode when you press them.
* **New Remote** - Start editing a new, empty remote.
* **Open Remote** - Open an existing remote file (REM) from the SD card.

## Button Edit UI

* **Name** - The button's text.
* **Path** - Select to pick a capture file.
* **Freq** - The center frequency to send on. Will default to the capture file's metadata if found.
* **Rate** - The sample rate of the capture file. Uses the capture file's metadata or defaults to 500K. Cannot be set in the UI.
* **Icon** - The icon to show on the button.
* **FG Color** - The button's foreground color.
* **BG Color** - The button's background color.
* **Preview** - Shows what the button will look like.
* **Trash** - Deletes this button and returns to the main screen.
* **Done** - Save this button and returns to the main screen.

## Tips
* Remotes are automatically saved on exit.
* Use the IQ Trim tool to trim silence from captures so they start instantly.

## REM Files
Remote files can be edited in a text editor.
Empty lines and lines starting with `#` are ignored.
The first non-ignored line is the remote "Title".
The remaining lines (up to 12) are read as remote buttons. They have the following format.

`capture path,button text,icon index,fg color index,bg color index,center frequency,samplerate`

The position of buttons on the screen can be changed by reordering lines in the REM file.

