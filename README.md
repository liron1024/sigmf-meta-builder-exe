# SigMF meta builder

Windows app that turns two Excel workbooks into RFix-style `.sigmf-meta` files, one per IQ recording.

This repository contains only the executable. Workbooks are read on your computer and are not uploaded anywhere.

## Run

1. Download [sigmf-meta-builder.exe](sigmf-meta-builder.exe).
2. Double-click it. Windows may ask you to keep the file because it was downloaded from the internet.
3. Your browser opens the app at http://127.0.0.1:4317. If that port is busy, the app picks the next free port.
4. Close the console window when you are finished. That stops the app.

Nothing else needs to be installed. Node.js and Go are not required.

## Use

1. Load the **BTS Hunter** workbook (one row per detected cell).
2. Load the **Cellular protocol** workbook (one row per IQ recording).
3. Leave the IQ datatype on `ci16_be` unless the recordings use another format.
4. In **Recording dates**, tick the days to include, or switch to **Range**.
5. Turn on **Hide empty files** to drop recordings that matched no cells.
6. Download one `.sigmf-meta` file from a row, or download every included file as `sigmf-meta.zip`.

A cell is written into a recording when one of its sightings is on that recording's day and its band overlaps the recording. Output names follow the IQ file name: `iq_…_0001.wav` becomes `iq_…_0001.sigmf-meta`.
