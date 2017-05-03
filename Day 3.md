# Installing StevenHickson Voice Command
## Install Git client

Script
```shell 
apt-get update
apt-get install git-y
```
Installing SH vocie recognition software
```shell
git clone git://github/StevenHickson/PiAUISuite.git
cd PiAUISuite/Install\
./InstallAUISuite.sh
```
Edit config file located in /home/pi/PiAUISite/VoiceCommand/commands.conf
```shell
light==/home/pi/scripts/led...
```

Tweakaudio settings to automatically enable the audio capbilities at boot
```shell
sudo apt-get update
sudo apt-get dist-upgrade -y
sudo apt-get install alsa-utils mpg321 lame -y
```
then enter command
```shell
sudo nano/etc/modules
```
Reboot Raspberry Pi.
Run following code
```shell
sudo amixer cset numid=3 1
sudo alsactl store
```
