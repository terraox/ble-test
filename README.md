# BLE printer test

A single-page tool (`index.html`) for testing TSPL printing over Bluetooth Low Energy using the Web Bluetooth API. There is nothing to install or build. You serve the folder on `localhost` and open it in a browser.

## Requirements

- Chrome or Edge on desktop. Safari and Firefox don't support Web Bluetooth.
- Bluetooth turned on on your computer.
- Python 3 (or Node.js) to run a local web server.
- The page must be opened from `http://localhost`. Double-clicking `index.html` won't work.
- Close every other app connected to the printer (phone app, nRF Connect). A BLE printer usually accepts one connection at a time.

## Step 1: Get the project

```bash
git clone <repo-url> ble-test
cd ble-test
```

## Step 2: Start a local server

Run one of these from inside the project folder.

### macOS

```bash
python3 -m http.server 8000
```

### Windows (PowerShell or Command Prompt)

```powershell
py -m http.server 8000
```

If `py` isn't found, try `python -m http.server 8000`.

### Alternative on either OS (Node.js)

```bash
npx serve -l 8000
```

## Step 3: Open the page

Go to <http://localhost:8000> in Chrome or Edge.

Or open it from the terminal:

- macOS: `open -a "Google Chrome" http://localhost:8000`
- Windows: `start chrome http://localhost:8000` (use `start msedge ...` for Edge)

## Step 4: Connect and print

1. Click **Connect to printer** and pick your printer in the browser dialog.
2. Set the label width, height and gap in mm (assumes 203 dpi).
3. Click **Print text label** or **Print bitmap test pattern**.
4. If the bitmap prints inverted (mostly black), switch **Dot polarity** and print again.

## Step 5: Tune speed (optional)

The default is 20-byte chunks with a 30 ms delay. Raise **Chunk bytes** (100, 180, 240) and lower **Delay ms** (10, 0) until printing becomes unreliable, then back off.

## Step 6: Stop the server

Press `Ctrl+C` in the terminal where the server is running.

## Troubleshooting

- **No device dialog or "Bluetooth not supported":** use Chrome or Edge, and make sure the page URL starts with `http://localhost`.
- **Port already in use:** change `8000` to another port, such as `8080`, in both the server command and the URL.
- **Can't connect:** disconnect the printer from other apps and power-cycle it.
