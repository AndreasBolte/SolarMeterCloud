# SolarMeterCloud

SolarMeterCloud captures and visualizes solar energy data in real time.  
The data is transmitted via MQTT, processed in Node‑RED, and automatically stored in Google Sheets.  
Published Google Sheets charts can be embedded into any HTTPS website using an iframe.

**Website:** https://colmuspro.eu  
**Contact:** info@colmuspro.eu

---

## Table of Contents
- [Features](#features)
- [Architecture](#architecture)
- [MQTT Topics](#mqtt-topics)
- [Google Sheets Integration](#google-sheets-integration)
- [Google Sheets Iframe](#google-sheets-iframe)
- [Firmware](#firmware)
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
**Sensor/Meter → Firmware → MQTT Broker → Node‑RED → Google Sheets → iframe Dashboard**

---

## MQTT Topics
- `h2QwryOD/Stromzähler/Solar/S30001` (voltage V)  
- `h2QwryOD/Stromzähler/Solar/S30007` (current A) 
- `h2QwryOD/Stromzähler/Solar/S30013` (active power W)  
- `h2QwryOD/Stromzähler/Solar/S30071` (frequency Hz)  
- `h2QwryOD/Stromzähler/Solar/S30073` (Import Energie kWh) 
- `h2QwryOD/Stromzähler/Solar/S30075` (Export Energie kWh)  

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
