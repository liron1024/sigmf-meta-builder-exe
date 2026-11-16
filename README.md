# SigMF meta builder

App that turns two Excel workbooks into RFix-style `.sigmf-meta` files, one per IQ recording.

This repository contains only the programs. Workbooks are read on your computer and are not uploaded anywhere. Nothing else needs to be installed.

## Windows

1. Download [sigmf-meta-builder.exe](sigmf-meta-builder.exe).
2. Double-click it. Windows may ask you to keep the file because it was downloaded from the internet.
3. Your browser opens the app at http://127.0.0.1:4317. If that port is busy, the app picks the next free port.
4. Close the console window when you are finished. That stops the app.

## Mac

Apple silicon MacBooks (M1 or newer) use [sigmf-meta-builder-mac](sigmf-meta-builder-mac). Older Intel MacBooks use [sigmf-meta-builder-mac-intel](sigmf-meta-builder-mac-intel). To see which one you have, open Apple menu → About This Mac. Chip says Apple M1, M2, M3, or M4 for the first file, and Intel for the second.

1. Download the file that matches the Mac.
2. Open Terminal, go to the download folder, and allow it to run:

```bash
cd ~/Downloads
chmod +x sigmf-meta-builder-mac
xattr -d com.apple.quarantine sigmf-meta-builder-mac
./sigmf-meta-builder-mac
```

Use `sigmf-meta-builder-mac-intel` in those commands instead if that is the file you downloaded.

3. Your browser opens the app at http://127.0.0.1:4317. If that port is busy, the app picks the next free port.
4. Press Control+C in the Terminal window when you are finished. That stops the app.

macOS may say the file is from an unidentified developer. The `xattr` command above clears the download block. If macOS still refuses, open System Settings → Privacy & Security and choose Open Anyway.

## Use

1. Load the **BTS Hunter** workbook (one row per detected cell).
2. Load the **Cellular protocol** workbook (one row per IQ recording).
3. Leave the IQ datatype on `ci16_be` unless the recordings use another format.
4. In **Recording dates**, tick the days to include, or switch to **Range**.
5. Turn on **Hide empty files** to drop recordings that matched no cells.
6. Download one `.sigmf-meta` file from a row, or download every included file as `sigmf-meta.zip`.

A cell is written into a recording when one of its sightings is on that recording's day and its band overlaps the recording. Output names follow the IQ file name: `iq_…_0001.wav` becomes `iq_…_0001.sigmf-meta`.
