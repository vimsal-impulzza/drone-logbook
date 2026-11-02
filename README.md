# Drone Flight Log

A single-page flight log and checklist for drone-in-a-dock operations. Fill it in from a phone, tablet, or laptop, then download the record as a PDF or an Excel file. No server, no account, no build step.

The interface is in Spanish.

## Features

- **Flight log** with sections for identification, equipment, mission, times, conditions, and results.
- **Flight ID** generated from the takeoff time to the second, for example `VUELO-20261102-105123`, so two flights never share an ID by accident.
- **Automatic calculations** for total flight duration and response time (alert to arrival), shown in hours, minutes, and seconds.
- **Checklist** with pre-flight, post-flight, and periodic sections. Each item is marked OK, Falla (failed), or N/A, and each section shows its progress and the number of failures.
- **Export** to PDF (flight log plus checklist) and to Excel (one sheet per part). Files are named after the flight ID.
- **Autosave** of the flight in progress, so a reload or an accidental tab close does not lose the work.
- **Remembered equipment:** pilot, drone, and dock carry over to the next flight.
- **Inline validation** for out-of-range values such as latitude, longitude, and battery percentage.
- **Light and dark appearance** that follows the system setting, a layout that works down to phone width, and keyboard and screen-reader support.

## Usage

1. Open the page. The takeoff time is filled with the current time, which defines the flight ID.
2. Complete the **Bitácora** tab and the **Checklist** tab. The **Ahora** button next to each time field fills in the current time.
3. Use **Descargar PDF** or **Descargar Excel** at the bottom of the page.
4. Use **Nuevo vuelo** to clear the flight and start another one.

To try it locally, open `index.html` in a browser. There is nothing to install.

## Data and privacy

Everything you enter stays in your browser (`localStorage`). Nothing is sent to any server.

- The autosaved draft and the remembered equipment are stored per browser and per device.
- Clearing site data, or using a private window, removes them.
- Download the PDF or the Excel file to keep a record. The browser is not an archive.

## Deploying to GitHub Pages

1. Push `index.html` to the root of the repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, and save.
4. After a minute or two the site is available at `https://<username>.github.io/<repository>/`.

On a free GitHub plan, Pages requires a public repository. Do not commit real mission data, locations, or other sensitive information.

## Third-party resources

The page loads these from a CDN, so exporting needs an internet connection the first time:

| Resource | Use | Source |
| --- | --- | --- |
| jsPDF 2.5.1 | PDF generation | cdnjs |
| jsPDF-AutoTable 3.8.2 | PDF tables | cdnjs |
| SheetJS (xlsx) 0.18.5 | Excel generation | cdnjs |
| IBM Plex Sans, Sans Condensed, Mono | Typography | Google Fonts |

The scripts are pinned to exact versions and verified with Subresource Integrity hashes. If you change a version, update its `integrity` attribute as well.

## Customizing

The form fields and checklist items are defined as plain data at the top of the script in `index.html` (`BITACORA` and `CHECKLIST`). Edit those two lists to add, remove, or reword fields and items. Colors, type, and spacing are CSS custom properties at the top of the stylesheet.

## Project structure

```
index.html   The whole app: markup, styles, and script
README.md    This file
.gitignore   Ignored files
```
