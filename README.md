# Do Good Multnomah: PPR Dashboard

A single-page Program Performance Report (PPR) dashboard for Do Good Multnomah. Upload the quarterly PPR Excel workbook and the dashboard builds itself from the workbook's `Detail` sheet.

Everything runs in the browser. The page has a Content-Security-Policy that forbids all data connections (`connect-src 'none'`), so the uploaded file cannot be sent anywhere, even if something malicious were injected.

## Features

- Drag-and-drop upload of a `.xlsx` / `.xls` PPR file
- Six views:
  - **Overview:** headline program metrics
  - **Demographics**
  - **Placements & Exits**
  - **Shelter & Housing Search**
  - **Programs**
  - **Client Detail / Print:** filterable client table, printable report, and Excel export
- "Load new file" button to swap in next quarter's workbook

## How to use

1. Open `index.html` in a browser (no build step or server needed).
2. Drag your PPR workbook onto the upload area, or click **Choose file**.
3. Switch between tabs to explore the data. Use **Client Detail / Print** to print or export.

To host it, enable GitHub Pages on this repository (Settings, Pages, branch `main`, folder `/root`) or deploy the single file to any static host.

## Required columns

The `Detail` sheet must include a header row containing `Client Unique Id`, plus these columns: `Household ID`, `HMIS Provider`, `Entry Date`, `Exit Date`, `Length of Stay (Leavers in FY)`, `Gender(894)`, `Race and Ethnicity(11203)`, `Age at Entry`, `Age Breakout_Standard`, `Veteran Status Crosswalk`, `Exit Destination`, `Exit Destination Crosswalk`, `Does the client have a disabling condition?(1212)`, `Relationship to Head of Household`, `Newly Served in FY`, `Newly Served Qtr_All People`, `BIPOC`, `Non-Hispanic White`, and `RaceEth Unreported`.

## Tech stack

- Plain HTML, CSS, and JavaScript in one file (`index.html`)
- [SheetJS](https://sheetjs.com/) to read and write Excel files and [Chart.js](https://www.chartjs.org/) for charts, loaded from cdnjs with Subresource Integrity hashes
- DM Sans and DM Mono from Google Fonts
- No backend

## Privacy and security

The PPR workbook can contain client-level HMIS data.

- **Nothing is uploaded.** Parsing happens locally, and the Content-Security-Policy blocks `fetch`, XHR, and beacons.
- **Spreadsheet text is escaped** before it is shown, so a cell containing HTML or script is displayed as plain text.
- **Do not commit real workbooks to this repository.** Anyone with the page URL can open the page (though not your files).
- If you change the CDN library versions, update the `integrity` hashes in `index.html`.

## Known gaps: numbers that are typed into the code

These sections show values from a past quarter that are written directly in `index.html`, not calculated from the uploaded file. They will be stale for any new upload until edited:

- Overview: the "1,837 total exits" and "529 total exits" subtitles
- Demographics: the "Primary language spoken" list (`langData`)
- Placements: the two "NP Drop-in" KPI cards and the whole "Permanent housing programs" card
- Shelter tab: the four length-of-stay boxes, the exit totals, and the Coordinated Access card

Search for `NOTE:` in `index.html` to find them.

## Project structure

```
index.html   Entire application: upload screen, dashboard, styles, and logic
```
