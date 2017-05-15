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
## Install Voice command library
```shell
sudo apt-get install libboost-regex1.49.0
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
Reboot Raspberry Pi,and run following code
```shell
sudo amixer cset numid=3 1
sudo alsactl store
```
## Configure USB Webcam Microphone on RASPBIAN
### Changes default adio input to be the Built0in Webcam Mic, and the default sound output to be the normal 3.5mm jack on the Raspberry Pi.
Edit alsa.conf file to set USB device as default.  Find lines "defaults.ctl.card 0" and replace the "0" with "1"
```shell
defaults.ctl.card 1
defaults.pcm.card 1
```
Next edit the ALSA configuration file .asoundrc. using nano to edit the file
```shell
sudo nano ~/.asoundrc
```
Script should look like
```shell
pcm.!default {
         type asym
         playback.pcm {
                 type plug
                 slave.pcm "hw:0,0"
         }
         capture.pcm {
                 type plug
                 slave.pcm "hw:1,0"
         } 
 }

 ctl.!default {
        type hw
        card 0
}
```
Test microphone following commands.
Record audio using
```shell
arecord test.wav
```
Play audio using
```shell
aplay test.wav
```
