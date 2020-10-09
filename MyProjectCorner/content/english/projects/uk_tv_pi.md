---
title: "Watch UK TV online outside of the UK"
sub_title: "Using a Raspberry Pi 4 and NordVPN"
date: 2020-09-01T23:27:48+02:00
slug: "watch-uk-tv-abroad"
images:
    -  /uk_tv_pi/uk-tv-pi-600.jpg
    -  /uk_tv_pi/uk-tv-pi-800.jpg
summary: "In this tutorial, I will show how to watch UK tv online from outside of the UK using a Raspberry Pi 4 and Nord VPN. By following the steps below it..."
description: "In this tutorial, I will show how to watch UK tv online from outside of the UK using a Raspberry Pi 4 and Nord VPN. By following the steps below it's possible to watch live and catch-up services from the four main networks (BBC, ITV, Channel 4 and Channel 5)"
btn_txt: "Set it up"
categories:
    - raspberry pi
---
{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

![Watch UK TV online outside of the UK on a Raspberry Pi 4 with NordVPN](/uk_tv_pi/uk-tv-pi-800.jpg)

***

In this tutorial, I will show how to watch UK tv online from outside of the UK using a Raspberry Pi 4 and Nord VPN.

By following the steps below it's possible to watch live and catch-up services from the four main networks (BBC, ITV, Channel 4 and Channel 5)

> Living in northern France we have always watched UK TV with FreeSat and a satellite dish pointed at the Astra satellite.
>
> However, our daughter left for university this year and wanted to continue watching her favorite TV channels (BBC, ITV, and Channel 4).
>
> Using several online sources I came up with this working solution.

***
{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

## Hardware I Used

- Raspberry Pi 4 - 4gb

- USB C Power Supply

- Micro SD Card (8gb class 10 min)

- A case for the Raspberry Pi 4

- Ethernet Cable (or use WiFi)

- Micro HDMI to HDMI cable

- Mouse & Keyboard

## Also Required

- NordVPN Subscription

***

## Install Raspberry Pi OS

Following the instructions on the official [**Raspberry Pi**](https://www.raspberrypi.org/downloads/ "Go to www.raspberrypi.org") website, and using the **Raspberry Pi Imager**, install the latest version of the **Raspberry Pi OS** desktop.

When complete, insert the SD card into the Pi, connect the screen, network cable (if using), mouse, and keyboard. Finally, plug in the power cable to power up.

>When connecting the screen use micro HDMI port 1 (closest to the USB-C power port), as this is the port with integrated HDMI sound.

Run through the setup process and then continue with this tutorial.

## Update the Raspberry Pi

```` shell
sudo apt-get update
````

```` shell
sudo apt-get dist-upgrade
````

***

## Install DRM support for Chromium

The standard installation of Buster on the Raspberry Pi comes with a version of the Chromium browser without [DRM](https://en.wikipedia.org/wiki/Digital_rights_management "DRM on Wikipedia") support.

DRM support is required to have access to certain streaming services

**1.** Enter the following line to download the installation script.  

``` shell
wget https://gist.githubusercontent.com/lemariva/0eb4ff4e847700627a5ebb71711c31bf/raw/0cab2916e4de65c0c5f780719221fdc052ac0bda/widevine-flash_armhf.sh
```

**2.** Make the downloaded file executable with

```` shell
chmod +x widevine-flash_armhf.sh
````

**3.** And execute the file with

```` shell
sudo ./widevine-flash_armhf.sh
````

***

## Install OpenVPN

**1.** Next, we want to install OpenVPN using the following command

```` shell
sudo apt-get install openvpn
````

**2.** When the installation is complete, change directory to openvpn

```` shell
cd /etc/openvpn/
````

***

## Set Up NordVPN

**1.** Download the NordVpn configuration files

```` shell
sudo wget https://nordvpn.com/api/files/zip
````

**2.** Unzip the downloaded file

```` shell
sudo unzip zip
````

**3.** Delete the downloaded zip file

```` shell
sudo rm zip
````

***

## Create an authentification text file

For automatic connection to NordVpn without the need to enter your username and password each time.

**1.** Create the auth.txt file

```` shell
sudo nano /etc/openvpn/auth.txt
````

**2.** Type your NordVpn username and password on separate lines

**3.** Press 'CTRL X' followed by 'Y' to save the file

***

## Configure the connection file

**1.** Enter the following command to list files in the current folder

```` shell
ls
````

**2.** Substitute 'uk1234' for your preferred (working) UK Vpn connection and copy to a new file

```` shell
sudo cp uk1234.nordvpn.com.udp1194.ovpn ukvpn.conf
````

**3.** Then open the copied file in the text editor

```` shell
sudo nano ukvpn.conf
````

**4.** Find the following line

```` shell
auth-user-pass
````

**5.** And change to

```` shell
auth-user-pass auth.txt
````

**6.** Press 'CTRL X' followed by 'Y' to save the file

>There are security issues related to storing usernames and passwords in a plain text file. Make sure your Raspberry Pi is secure.

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}

{{< section_main >}}
{{< section "-sub" >}}

{{< section "-top" >}}
{{% section_textbox "-pi" %}}

## Set OpenVPN to connect on startup

**1.** In the text editor open the OpenVPN configuration file

```` shell
sudo nano /etc/default/openvpn
````

**2.** Find the line

```` shell
#AUTOSTART="all"
````

**3.** Uncomment (remove the leading #) and change "all" to "ukvpn"

```` shell
AUTOSTART="ukvpn"
````

**4.** Press 'CTRL X' followed by 'Y' to save and close the file

***

## Reboot the Pi and check the connection

```` shell
sudo reboot
````

Open Chrome and go to [NordVPN](www.nordvpn.com "Go to NordVPN website") or  [What's my IP](https://whatismyipaddress.com/ "Check with What's My Ip website") and check your public IP address. It should now show your location as the UK.

***

## Set up the TV channels

>To use the online UK streaming services you will need to register on each of the websites. To do this you will require a valid email account. I set up a new Yahoo email to do this.

Start by creating a desktop shortcut to the newly installed DRM Chromium browser

[![Adding Chromium DRM browser shortcut to Pi desktop](/uk_tv_pi/uk-tv-pi01-600.jpg)](/uk_tv_pi/uk-tv-pi01.jpg)

Use the desktop shortcut to open the DRM browser and visit the following links to sign up

- [BBC IPlayer](https://www.bbc.co.uk/iplayer "Link to BBC IPlayer")

![BBC IPlayer webpage](/uk_tv_pi/bbc-iplayer-600.jpg)

- [ITV Hub](https://www.itv.com/hub/itv "Link to ITV Hub")

![ITV Hub webpage](/uk_tv_pi/itv-hub-600.jpg)

- [All 4](https://www.channel4.com/now/C4 "Link to All 4")

![All 4 webpage](/uk_tv_pi/all-4-600.jpg)

- [My 5](https://www.my5.tv/ "Link to My 5")

![My 5 webpage](/uk_tv_pi/my-5-600.jpg)


>Follow the instructions to sign up for each of the channels. You will be required to supply a UK postcode and to verify your email to create an account.
>
>When logged in, bookmark the site and add to the bookmark bar to make it easy to return.

***

## Now you can watch live and catch up UK Television from anywhere in the world

***

{{% /section_textbox %}}
{{< /section >}}

{{< /section >}}
{{< /section_main >}}

{{< adsense_hr >}}
