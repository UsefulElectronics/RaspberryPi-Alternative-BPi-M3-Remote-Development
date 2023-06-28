
[![Build Status](https://img.shields.io/badge/USEFUL%20ELECTRONICS-YOUTUBE-red)](https://www.youtube.com/user/wardzx1)

# Sponsors

### PCBWay
Tutorial Series Sponsor PCBWay Website. You can get extra free coupons using the link below:

[<img src="https://github.com/UsefulElectronics/RaspberryPi-Alternative-BPi-M3-Remote-Development/blob/main/Pictures/250x250.gif">](https://www.pcbway.com/setinvite.aspx?inviteid=582640)


# RaspberryPi-Alternative-BPi-M3-Remote-Development

### [Tutorial Link](https://youtu.be/54qtV8BrDjk) On [![Build Status](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/wardzx1) 

In this tutorial, I am sharing with you guys my experience with BPI-M3 development board from BananaPi, which runs with Armbian image. Several methods are used to connect remotely to the BPI-M3. 

Minicom: used to connect to the board over UART
If the network connection is available:
SSH: used to connect remotely from the terminal 
XRDP: Remote Desktop Protocol
Webmin: web based system administration allows remote access over browser 

This tutorial is a very good introduction to learn embedded linux development;

Balena Etcher image flashing program:
https://etcher.balena.io/

Armbian OS Image for BPI-M3:
https://drive.google.com/file/d/1zKjbj9iwoCgbaPCImjQ44P4zLBHAB7di/view?usp=sharing

To install Minicom on ubuntu OS, run the following command 

```sh
sudo apt-get install minicom
```
After installation, you can change the minicom settings:

```sh
sudo minicom -s 
```

To connect over UART to your board, execute:

```sh
sudo minicom --device dev/(UART port) --boaudrate 115200
```

(UART port) needs to be changed depending on your serial port. It is posible to check port number using this command:
```sh
dmesg | grep tty
```

In order to scan the surrounding WiFi network you need to use network-manager command:
```sh
nmcli device wifi list
```
Use this command to connect to you network over WiFi:
```sh
nmcli device wifi connect "$SSID" password "$PASSWORD"
```
Having connected successfully over WiFi, now it is possible to connect to you baord remotely using SSH.
It is possible to checkyour board IP address by accessing your WiFi router and check the clint list. Of course, after making executing connection request after SSH you will be asked to enter your password.
```sh
ssh USERNAME@IP  //pi@192.168.1.102
```

If your image has desctop and you are on windows, you can access your board OS desctop using Xrdp. To insatall Xrdp package use the followng commands:
```sh
sudo apt install xrdp 
```
```sh
sudo apt install xrdp xorgxrdp
```

In order to let Xrdp service run automatically after reboot use systemctl command. Note that you can use systemctl command with every service:
```sh
sudo systemctl enable xrdp
```

Check service status:
```sh
sudo systemctl status xrdp
```

Restart service:
```sh
sudo systemctl restart xrdp
```

webmin allows you to connect to your board over browser. This can  be useful espesially if your OS does not have  desctop. To install webmin:
```sh
wget https://prdownloads.sourceforge.net/webadmin/webmin_1.962_all.deb
```
```sh
sudo dpkg -i webmin_1.962_all.deb 
```
```sh
sudo apt -f install
```

![Circuit Diagram](https://github.com/UsefulElectronics/RaspberryPi-Alternative-BPi-M3-Remote-Development/blob/main/Pictures/hardware.PNG)
***

