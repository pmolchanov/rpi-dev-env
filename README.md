## Overview

Quick start to get a minimalist web development environment up and running on a Rasperry Pi


## Configuration

* Raspberry Pi 4 B 8GB
* Logitech K360 Keyboard
* Logitech M310 Mouse
* ViewSonic VA1665 Montior


## Mouse & Keyboard

* Use Logitech Unifying software on a PC or Mac to pair the USB receiver with the keyboard and mouse


## Flash SD card using Raspberry Pi Imager 

* Operating System: Raspberry Pi OS Lite (32-bit)
* Advanced Options: configure username and password, set locale settings


## Connect to WiFi

* `sudo raspi-config`
* select Advanced Options >> Network Config >> Network Manager
* exit and reboot
* `nmtui`
* select Activate a connection
* choose a Wi-Fi Network


## Update Package Cache & Packages
```
sudo apt update
sudo apt upgrade
```


## Get sound working

By default, audio is output on the headphone jack. We need it output on HDMI0. 

* `sudo apt install pulseaudio pavucontrol`
* reboot
* `sudo raspi-config`
* select System Options >> Audio >> 1 MAI PCM 12s-hifi-0
* `speaker-test`


## Install i3 Window Manager, and configure it to start at login
* `sudo apt install xserver-xorg xinit i3`
* `startx`
* generate an i3 config
* `vi ~/.config/i3/config`
* add at the end of the file:
```
# customizations
workspace_layout tabbed
```
* `vi ~/.profile`
* add at the end of the file:
```
# start X on login
if [ -z "${DISPLAY}" ] && [ "${XDG_VTNR}" -eq 1 ]; then
  exec startx
fi
```
* reboot


## Add additional utility software

### File Manager
`sudo apt install thunar thunar-archive-plugin`

### Browser
`sudo apt install chromium-browser`

### Git
* `sudo apt install git`
* `git config --global user.name "Your Name"`
* `git config --global user.email "youremail@yourdomain.com"`

### GitHub
* Place SSH keys in `~/.ssh/github.com` folder
* `sudo chmod 600 ~/.ssh/your_private_key`
* `vi ~/.ssh/config`
* add at the end of the file:
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/github.com/your_private_key
  IdentitiesOnly yes
```

### VSCode
 `sudo apt install code`

### NodeJS
```
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install nodejs
```

### mitmproxy

Installation

* `sudo apt install python3-pip`
* `sudo pip3 install mitmproxy`

Install Root CA certificate
* `mitmweb --no-open-web-browser`
* `chromium-browser --proxy-server=localhost:8080`
* Download Linux root certificate from `http://mitm.it`
* Follow installation instructions
* Navigate to `chrome://settings/certificates`
* Select the Authorities tab
* Click the Import button  


### Password Manager
`sudo apt install keepassxc`
