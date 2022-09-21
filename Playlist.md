This app allows users to create playlists of previously captured signals and replay them in a specific order. The playlist app shares a UI with the [Replay app](https://github.com/eried/portapack-mayhem/wiki/Replay).

A sample playlist.txt file is included in the SD card samples.

Playlist files are comma delimited and have the following structure:

FREQ,File_PATH,SAMPLE_RATE

For example, a valid playlist file could contain:

    ##FREQ      FILE				 SAMPLE RATE
    315000000,SAMPLES/TeslaChargePort_US.C16,500000
    433920000,SAMPLES/TeslaChargePort_EU_AU.C16,500000

Note that lines beginning with # are treated as comments and ignored.

[Video demonstration of playlist app](https://user-images.githubusercontent.com/164560/191515258-36621648-3827-4eed-b77b-e8dbaf9be63e.mov)
