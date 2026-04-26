# SolarMeterCloud

SolarMeterCloud captures and visualizes solar energy data in real time.  
The data is transmitted via MQTT, processed in Node‑RED, and automatically stored in Google Sheets.  
Published Google Sheets charts can be embedded into any HTTPS website using an iframe.

**Website:** <https://colmuspro.eu>  
**Contact:** <info@colmuspro.eu>

---

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [MQTT Topics](#mqtt-topics)
- [Google Sheets Integration](#google-sheets-integration)
- [Google Sheets Iframe](#google-sheets-iframe)
- [Firmware/raspberry-pi/hardware-setup](./firmware/raspberry-pi/hardware-setup.md)
- [Firmware/raspberry-pi/software-setup](./firmware/raspberry-pi/software-setup.md)
- [Important Safety Notice](#important-safety-notice)
- [License](#license)

---

## Features

- Real‑time solar power measurement  
- MQTT data transmission  
- Node‑RED dashboard & processing  
- Automatic export to Google Sheets  
- Public charts via iframe  
- Long‑term cloud storage  

---

## Architecture

Sensor/Meter → Firmware → MQTT Broker → Node‑RED → Google Sheets → iframe Dashboard**

---

## MQTT Topics

- `SolarMeterCloud/Solar/Meter/VoltageS30001` (V)  
- `SolarMeterCloud/Solar/Meter/CurrentS30007` (A)  
- `SolarMeterCloud/Solar/Meter/ActivePowerS30013` (W)  
- `SolarMeterCloud/Solar/Meter/FrequencyS30071` (Hz)  
- `SolarMeterCloud/Solar/Meter/ImportEnergyS30073` (kWh)  
- `SolarMeterCloud/Solar/Meter/ExportEnergyS30075` (kWh)  

---

## Google Sheets Integration

- **setupFirstStep.md** – Basic setup (required)  
- **setupAdvancedStatistics.md** – Advanced charts, formatting, and embedding  

---



## Google Sheets Iframe

1. In Google Sheets: **File → Publish to the web**  
2. Select the chart  
3. Copy the iframe link and embed it into your website  

**Example:**

```html
<iframe src="https://docs.google.com/.../pubchart" width="100%" height="500"></iframe>
```

---

## Node-RED Flow

The complete Node‑RED flow is located in the folder [`docs/flows`](docs/flows):

- [SolarMeterCloud Flow](docs/flows/solarmetercloud-flow.json)

This file can be imported directly into Node‑RED.

## Important Safety Notice

Work on electrical installations may only be carried out by qualified electricians. No liability is assumed for the application of the content presented here.

---

## Required Node-RED Modules

This project uses Node‑RED Projects Mode. All required palette modules are listed in the `package.json` file:

- [`package.json`](package.json)

To install all dependencies, run the following command inside the project directory:

```bash
npm install
```
