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
3. Ensure that python3 and pip are installed with the commands:\
   \
   `sudo apt install python3 pip`
4. The script requires several dependencies, install them with 


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
