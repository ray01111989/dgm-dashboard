# Do Good Multnomah: PPR Dashboard

A single-page Program Performance Report (PPR) dashboard for Do Good Multnomah. Upload the quarterly PPR Excel workbook and the dashboard builds itself from every sheet.

Everything runs in the browser. The app makes no network requests for data, so the uploaded file is not sent anywhere.

## Features

- Drag-and-drop upload of a `.xlsx` / `.xls` PPR file
- Reads all sheets automatically (All Programs, Perm Housing, Shelter, Detail)
- Six views:
  - **Overview:** headline program metrics
  - **Demographics**
  - **Placements & Exits**
  - **Shelter & Housing Search**
  - **Programs**
  - **Client Detail / Print:** printable client detail report
- "Load new file" button to swap in next quarter's workbook

## How to use

1. Open `index.html` in a browser (no build step or server needed).
2. Drag your PPR workbook onto the upload area, or click **Choose file**.
3. Switch between tabs to explore the data. Use **Client Detail / Print** to produce the printable report.

To host it, enable GitHub Pages on this repository (Settings, Pages, branch `main`, folder `/root`) or deploy the single file to any static host.

## Tech stack

- Plain HTML, CSS, and JavaScript in one file (`index.html`)
- Client-side Excel parsing and chart rendering, with no backend

## Privacy

The PPR workbook can contain client-level HMIS data. Because parsing happens locally in the browser, nothing is uploaded, but **do not commit real workbooks to this repository** and be careful when hosting it on a public URL, since anyone with the link can open the page (though not your files).

## Project structure

```
index.html   Entire application: upload screen, dashboard, styles, and logic
```
