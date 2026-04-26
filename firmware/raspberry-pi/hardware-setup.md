📦 Raspberry Pi + Accessories + RS485 Adapter (Technical Overview)

🧩 Raspberry Pi

Model: Raspberry Pi 5

Architecture: 64‑bit

Memory: 4 GB RAM or more recommended

Note:

Additional RAM provides headroom for Node‑RED flows, MQTT broker, Modbus communication, and Google Sheets integration.



🔌 Power Supply

Type: Original Raspberry Pi power supply

Connector: USB‑C

Voltage: 5 V

Current: 5 A

Note: Required for stable operation of the Raspberry Pi 5.



💾 Storage

Type: microSDHC

Capacity: 16–32 GB

Speed: Class 10 or higher

Purpose: Operating system and Node‑RED data



🔌 USB‑to‑RS485 Adapter

Type:

# USB‑RS485 Adapter

For Modbus‑RTU communication between the Raspberry Pi and the SDM120 energy meter, the following adapter type is used:

**Waveshare Industrial USB to RS485 Converter**  
with **FT232RNL** (USB‑UART) and **SP485EEN** (RS485 transceiver)

## Key Features

- Original **FT232RNL** USB‑UART chip  
- **SP485EEN** industrial‑grade RS485 transceiver  
- Automatic transceiving (no manual DE/RE control required)  
- Embedded protection circuits:  
  - Resettable fuse  
  - ESD protection  
  - TVS diode  
- Screw terminals for A/B/GND  
- Robust industrial enclosure  
- Fully compatible with Raspberry Pi OS  
- Detected as `/dev/ttyUSB0` (or `/dev/ttyUSB1` if multiple devices are connected)

## Connection Overview





Purpose:

Required for Modbus RTU communication with the SDM120 energy meter.



📘 Raspberry Pi Setup (SolarMeterCloud)

1\. Clone the Repository

bash

git clone https://github.com/AndreasBolte/SolarMeterCloud.git

Use a laptop to prepare the microSD card.

A micro‑SD adapter is required.



2\. Network Configuration

Set a static Wi‑Fi IP address using the Raspberry Pi OS desktop network icon.



Configure the wlan interface accordingly.



3\. System Update

bash

sudo apt update

sudo apt full-upgrade

4\. Firmware Update (Optional)

bash

sudo rpi-update

sudo reboot

5\. Install XRDP (Remote Desktop)

bash

sudo apt-get install xrdp

6\. Raspberry Pi Configuration

Open configuration tool:



bash

sudo raspi-config

System Information

Detected system (example):

Raspberry Pi 5 Model B Rev 1.1, 8GB



Enable Serial Port (Modbus RS485)

Code

3 Interface Options

I6 Serial Port

Disable login shell over serial → No



Enable serial hardware → Yes



Disable Bluetooth (optional)

bash

echo "dtoverlay=disable-bt" | sudo tee -a /boot/config.txt

sudo systemctl disable hciuart

sudo reboot

Adjust permissions for serial device (example)

bash

sudo chmod 666 /dev/ttyACM0

7\. Install usbmount (optional)

bash

sudo apt-get install usbmount

8\. Disable Auto‑Login for RDP

Code

1 System Options

S6 Auto Login → Disabled

9\. Install Node‑RED (via Snap)

Snap avoids issues with npm and Node.js versions.



bash

sudo apt update

sudo apt install core

sudo apt install snapd

sudo reboot

Install Node‑RED:



bash

sudo snap install node-red --stable

10\. Node‑RED Settings

Settings file location:



bash

cd /var/snap/node-red/884

sudo nano settings.js

Enable:



contextStorage



user authentication (optional)



Example:



Code

name: pi

password: XXXXX

11\. Install Putty (optional)

bash

sudo apt-get install aptitude

sudo apt install putty

12\. Install MQTT Broker (Mosquitto)

bash

sudo apt install mosquitto mosquitto-clients

sudo systemctl enable mosquitto

Start/stop:



bash

sudo systemctl start mosquitto

sudo systemctl stop mosquitto

sudo systemctl status mosquitto

MQTT Configuration (no authentication)

Create config file:



bash

sudo nano /etc/mosquitto/conf.d/local.conf

Add:



Code

listener 1883

allow\_anonymous true

Reboot:



bash

sudo reboot

