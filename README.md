# RF Survey Visualizer

A browser-based tool for visualizing passive WiFi survey data collected during security audits and network assessments. Built as a single HTML file with zero dependencies to install — just open and go.

---

## What It Does

Loads WiGLE-format CSV files from wardriving hardware (tested with M5Stack Cardputer running Bruce firmware) and renders an interactive map showing nearby wireless networks with encryption type, signal strength, GPS location, and audit status tagging.

Built for home network security audits and RF environment awareness — identifying open networks, weak encryption, and IoT device exposure in a given area.

---

## Features

- **Drag and drop CSV loading** — drop one or multiple wardriving CSVs directly onto the map
- **Multi-run support** — compare multiple wardriving sessions side by side, each with a unique color trail
- **Live search** — search any SSID or MAC address with auto-zoom to result
- **Encryption filtering** — filter by All / Open / WPA2 / WPA3 / WPA with one click
- **Heatmap mode** — toggle between dot markers and an RF density heatmap
- **Route visualization** — GPS trail showing your wardriving path per session
- **Audit status tagging** — mark networks as Cracked / Attempted / Target directly on the map
- **Dark map theme** — CartoDB dark tiles for low-light readability
- **Zero install** — single HTML file, no server, no build step, no dependencies

---

## Hardware

Tested with the following wardriving setup:

| Component | Details |
|---|---|
| Device | M5Stack Cardputer ADV |
| Firmware | Bruce 1.14+ |
| GPS Module | Cap LoRa-1262 (GNSS) |
| Output Format | WiGLE CSV v1.6 |

Any hardware that outputs WiGLE-compatible CSV format will work.

---

## Usage

### Quick Start

1. Download `index.html`
2. Open it in any modern browser (Chrome, Firefox, Edge)
3. Drag your wardriving CSV file(s) onto the drop zone
4. Click **Launch Map**

### Adding More Runs

Drag additional CSV files directly onto the live map at any time — new runs load instantly without refreshing.

### Searching

Type any SSID or MAC address in the search bar. The map auto-zooms to the first matching result and shows a results count badge.

### Filtering

Click **Open**, **WPA2**, **WPA3**, or **WPA** to filter by encryption type. Combine with search for precise results.

### Audit Tagging

Click any network marker to open a popup. Use the action buttons to tag the network status:

| Tag | Meaning | Color |
|---|---|---|
| **Cracked** | Password successfully recovered | Green ring |
| **Tried** | Attempted but not cracked | Orange ring |
| **Target** | Flagged for future attempt | Red ring |
| **Clear** | Remove status tag | — |

Tags persist for your session. Refresh to clear all tags.

### Heatmap

Click **Heatmap** in the top bar to toggle between individual network markers and an RF density heatmap showing coverage intensity across your survey area.

---

## CSV Format

This tool expects WiGLE WiFi CSV format (v1.6), which is the default output from Bruce firmware wardriving mode. The file should start with:

```
WigleWifi-1.6,appRelease=...
MAC,SSID,AuthMode,FirstSeen,Channel,Frequency,RSSI,CurrentLatitude,CurrentLongitude,...
```

---

## Security Notice

**Never commit wardriving data to this repository.** The `.gitignore` is pre-configured to block all CSV, PCAP, and handshake files. Before pushing, verify:

```bash
git status
```

Ensure no `.csv`, `.pcap`, `.hc22000`, or credential files appear in the staged changes.

Wardriving data contains your neighbors' network names, MAC addresses, and GPS locations. Treat it as sensitive data.

---

## Ethical Use

This tool is intended for:

- Home network security self-assessment
- Authorized RF site surveys
- Security research and education
- Network infrastructure awareness

Do not use this tool to access networks you do not own or have explicit authorization to test. Unauthorized network access is illegal under the Computer Fraud and Abuse Act (CFAA) and equivalent laws in other jurisdictions.

---

## Tech Stack

| Component | Technology |
|---|---|
| Map rendering | Leaflet.js 1.9.4 |
| Tile layer | CartoDB Dark Matter |
| Heatmap | Leaflet.heat 0.2.0 |
| Language | Vanilla JavaScript (ES5) |
| Styling | CSS custom properties |
| Build | None — single file |

---

## License

MIT License — free to use, modify, and distribute.

---

## Author

Built as part of a home network security audit project using the M5Stack Cardputer ADV and Bruce firmware.
