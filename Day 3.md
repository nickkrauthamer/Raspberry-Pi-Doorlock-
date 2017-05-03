# Installing StevenHickson Voice Command
## Install Git client

Script
```shell 
apt-get update
apt-get install git-y
```
#3 Install the WiringPi Library to send and reveive data through the GPIO pins using high level languages like shell or python
```shell
cd~/
git clone git://git.drogon.net/wringPI
cd wiringPi
./build
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
