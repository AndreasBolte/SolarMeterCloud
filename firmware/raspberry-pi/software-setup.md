Raspberry Pi Setup (SolarMeterCloud)



1\. Clone the Repository

&#x20;  git clone https://github.com/AndreasBolte/SolarMeterCloud.git

&#x20;  Use a laptop to prepare the microSD card. A micro-SD adapter is required.



2\. Network Configuration

&#x20;  Set a static Wi-Fi IP address using the Raspberry Pi OS desktop network icon.

&#x20;  Configure the wlan interface.



3\. System Update

&#x20;  sudo apt update

&#x20;  sudo apt full-upgrade



4\. Firmware Update (Optional)

&#x20;  sudo rpi-update

&#x20;  sudo reboot



5\. Install XRDP

&#x20;  sudo apt-get install xrdp



6\. Raspberry Pi Configuration

&#x20;  sudo raspi-config

&#x20;  Enable serial port: No for console, Yes for serial hardware.

&#x20;  Disable Bluetooth:

&#x20;    echo "dtoverlay=disable-bt" | sudo tee -a /boot/config.txt

&#x20;    sudo systemctl disable hciuart

&#x20;    sudo reboot

&#x20;  Adjust permissions:

&#x20;    sudo chmod 666 /dev/ttyACM0



7\. Install usbmount (optional)

&#x20;  sudo apt-get install usbmount



8\. Disable Auto-Login for RDP

&#x20;  System Options -> Auto Login -> Disabled



9\. Install Node-RED via Snap

&#x20;  sudo apt update

&#x20;  sudo apt install core

&#x20;  sudo apt install snapd

&#x20;  sudo reboot

&#x20;  sudo snap install node-red --stable



10\. Node-RED Settings

&#x20;   cd /var/snap/node-red/884

&#x20;   sudo nano settings.js

&#x20;   Enable contextStorage and optional user authentication.



11\. Install Putty (optional)

&#x20;   sudo apt-get install aptitude

&#x20;   sudo apt install putty



12\. Install MQTT Broker (Mosquitto)

&#x20;   sudo apt install mosquitto mosquitto-clients

&#x20;   sudo systemctl enable mosquitto

&#x20;   sudo systemctl start mosquitto



&#x20;   MQTT Configuration (no authentication):

&#x20;   sudo nano /etc/mosquitto/conf.d/local.conf

&#x20;   listener 1883

&#x20;   allow\_anonymous true

&#x20;   sudo reboot



