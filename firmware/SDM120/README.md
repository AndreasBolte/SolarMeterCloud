# SDM120 – Modbus Dokumentation

## Offizielle Datenblätter & Protokolle

- SDM120 Series Multifunction Manual (Eastron Europe)  
  https://www.eastroneurope.com/ (→ Dokument: SDM120 Series Multifunction Manual)

- SDM120 Modbus Protocol Documentation  
  https://www.eastroneurope.com/ (→ Dokument: SDM120 Modbus Protocol)

- SDM120 Modbus User Manual (Mirror)  
  https://www.manualslib.com/manual/XXXXX/ (SDM120 Modbus User Manual)

  # SDM120 Modbus Configuration

The following settings apply to the SDM120 energy meter used in the SolarMeterCloud measurement architecture.  
They follow the official manufacturer specifications and are optimized for Modbus RTU via a USB‑RS485 adapter.

## Serial Interface Parameters

| Parameter      | Value         | Description |
|----------------|---------------|-------------|
| Serial Type    | RTU-BUFFERED  | Modbus RTU with buffered reception |
| Baud Rate      | 9600          | Default SDM120 baud rate |
| Data Bits      | 8             | Standard Modbus configuration |
| Stop Bits      | 1             | Standard Modbus configuration |
| Parity         | None          | No parity |

These settings must be identical on the SDM120, the USB‑RS485 adapter, and in Node‑RED.

## Node-RED Modbus Client (Measurement Pi)

### Modbus Client Node

- Type: Serial  
- Serial Port: `/dev/ttyUSB0`  
- Baud Rate: `9600`  
- Data Bits: `8`  
- Stop Bits: `1`  
- Parity: `none`  
- Serial Type: `RTU-BUFFERED`  
- Timeout: 1000–2000 ms  
- Retries: 1–3  
- Delay Between Messages: 50–100 ms
