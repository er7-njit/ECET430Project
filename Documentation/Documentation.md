# User Documentation

**DISCLAIMER: The Pi Tracker is still in development, the steps outlined here are for setup in uses related to development ONLY. The Pi Tracker is not supported, or recommended for use in production environments**

### Table of Contents
1. Supported Hardware
2. Device Summary
3. Basic Setup and Operation
4. Troubleshooting steps

## Supported Hardware
**Microcontrollers**:
- Raspberry Pi Zero W\
\
**OS Support**:
- Pi OS Lite\
\
**GPS Support**:
- Adafruit Ultimate GPS\
\
**WWAN Module Support**:
- Sierra Wireless EM7455

## Device Summary
The Pi Tracker is a tracking device that utilizes an Adafruit GPS module and a Sierra EM7455 WWAN Module to wirelessly transmit its location to the cloud. Its base componentry is a Pi Zero W (Figure 1), Adafruit Ultimate GPS attached by USB (Figure 2), and Sierra EM7455 WWAN Interface (FIgure 3) attached via a miniPCIe to USB adapter. Both of these interfaces are attached to a USB hub, which is connected to the Pi. 

## Basic Setup and Operation
**Device Assembly**
###
Firstly, connect the GPS and WWAN Module to the USB Hub. Then, connect the USB hub to the inner USB OTG port of the Pi Zero. Finally, connect the Pi to USB power using the outside USB port. 
###
**Device Setup**
###
1. Using the [Raspberry Pi Imager](https://www.raspberrypi.com/software/), flash Pi OS Lite onto an SD Card with a recommended size of 16GB or greater. Ensure that SSH and Wi-Fi settings are configured such that you can access the Pi via SSH.
2. Ensure the the Pi's software is fully up to date with the commands:\
   \
   `sudo apt update && sudo apt upgrade -y`
3. Ensure that nmcli, python3 and pip are installed with the commands:\
   \
   `sudo apt install python3 pip nmcli`
4. Configure APN Settings for SIM Card using nmcli:\
   ```
   sudo nmcli c add type gsm ifname <interface> con-name <name> apn <operator_apn>
   sudo nmcli connection up id <name>
   ```
   _Change <interface> to the corresponding interface name for your wwan module, as per ip link_\
   _Change <name> to your desired name for the connection, and <operator_apn> to your operator's APN_
6. The script requires several dependencies, install them within a python environment as root
   \
   `pip install board pytz adafruit-circuitpython-gps`
7. Clone this repository to an accesible folder in the home directory
8. cd to the scripts folder
9. Edit the script emailgps.py with your editor of choice
10. Change the variable `EMAIL_SENDER` to your email of choice
11. Run the script
12. Wait for fix and recieve the coordinates of the Pi Tracker at the chosen email and printed in the terminal
\
## Troubleshooting Steps
## Issues with Network
**Unable to Connect to Cellular Network**
- Ensure that the card is fully connected to the adapters and Pi
- Ensure the APN settings are configured using nmcli
- Ensure you are in an area of good cellular range

**Unable to Communicate with Pi via SSH**
- Ensure the Pi is connected to your LAN via the use of an IP Scanner or accessing your router's client list. Alternatively, you can plug in a monitor and peripherals and run iwconfig and a ping test.
- Ensure SSH is enabled on the Pi when flashing the image or using peripherals and a display. Alternatively, SSH can be enabled directly on the SD card. More information about this available [here](https://roboticsbackend.com/enable-ssh-on-raspberry-pi-raspbian/)

## Issues with GPS
**Unable to gain GPS Fix**
- Ensure the GPS has solid physical connection to the Pi, and that the Rx and Tx lights are illuminated and flashing, indicating data transmission and reception.
- Ensure the GPS is in a location that would have good GPS reception.

### Referenced Material
![Screenshot From 2024-12-22 21-57-38](https://github.com/user-attachments/assets/cc25fb00-368d-45e4-8d2e-35eac3726188)
### **Figure 1**
###
![image](https://github.com/user-attachments/assets/a06c838b-ccc5-40c2-9f87-509b749f7762)
### **Figure 2**
###
![image](https://github.com/user-attachments/assets/eb47f7e1-366b-4ecb-9ad9-89c11270a051)
### **Figure 3**
###
