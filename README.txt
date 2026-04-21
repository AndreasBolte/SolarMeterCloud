SolarMeterCloud

SolarMeterCloud erfasst und visualisiert Solardaten in Echtzeit.  
Die Daten werden per MQTT übertragen, in Node‑RED verarbeitet und automatisch in Google Sheets gespeichert.  
Veröffentlichte Google‑Sheets‑Diagramme können als iframe in jede HTTPS‑Website eingebunden werden.

Website: https://colmuspro.de
Kontakt: info@colmuspro.de

------------------------------------------------------------
FUNKTIONEN
------------------------------------------------------------
- Echtzeit‑Messung von Solarstrom
- MQTT‑Datenübertragung
- Node‑RED Dashboard & Verarbeitung
- Automatischer Export zu Google Sheets
- Öffentliche Diagramme per iframe
- Langzeit‑Cloud‑Speicherung

------------------------------------------------------------
ARCHITEKTUR
------------------------------------------------------------
Sensor/Meter → Firmware → MQTT Broker → Node‑RED → Google Sheets → iframe Dashboard

------------------------------------------------------------
MQTT TOPICS
------------------------------------------------------------
solarmetercloud/power   (Wirkleistung)
solarmetercloud/energy  (Energie kWh)
solarmetercloud/status  (Status)
solarmetercloud/debug   (Debug)

------------------------------------------------------------
GOOGLE SHEETS IFRAME
------------------------------------------------------------
1. In Google Sheets: "Datei → Veröffentlichen im Web"
2. Diagramm auswählen
3. iframe‑Link kopieren und in Website einfügen

Beispiel:
<iframe src="https://docs.google.com/.../pubchart" width="100%" height="500"></iframe>

------------------------------------------------------------
FIRMWARE
------------------------------------------------------------
- Liest Messwerte (S0, Modbus, etc.)
- Sendet Daten per MQTT
- Konfiguration: WLAN, Broker, Intervalle

------------------------------------------------------------
LIZENZ
------------------------------------------------------------
GNU General Public License v3.0 (GPL‑3.0)
