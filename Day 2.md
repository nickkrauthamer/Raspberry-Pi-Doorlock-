# Turn on LED via Raspberry Pi 

# Downloading Vocie StevenHickson Voice Activation
## Initializing
Check whether microphone or webcam is detected by Raspberry Pi and the microphone volumes are high. First step is to check webcam and microphone are listed using the following command
```shell
lsusb
```
Next set microphone recording volume to high by entering the follwoing command 
```shell
alsamixer
```
press the up or down arrow keys to set the volume. Press F6 and then select the webcam or microphone from the list and use the up arrow key to set recording colume to high.

## Connecting Raspberry Pi to breadboard and LED
connect a black female to male jumper to physical pin 6, a ground pin and connect red jumper to physical pin 16 of your pi

## Install Wiring Pi
Wiring Pi is used to switch the GPIO pins high and low.
Download instructions
```shell
sudo apt-get install git-core
gir clone gt://git.drogon.net/wiringPI
cd wiringPi
./build
```
The next step is to create the followng script as a file named 'led'
```shell
#!/bin/bash

if [ $# > 1 ]

then

/usr/local/bin/gpio mode 4 out

if [[ "$1" = "on" ]]

then

/usr/local/bin/gpio write 4 on

fi

if [[ "$1" = "off" ]]

then

/usr/local/bin/gpio write 4 off

fi

fi

Set the script to be executable with the following command:

chmod u+x led
```
To turn on the LED connected to the pin enter the command
```shell
./led on
```
To turn off the LED use command
```shell
./led off
```
Connect LED to breadboard using two jumper cables to pin 6 and 12 on the pi

Use 330 ohm resistor to limit the current flow.

Final Script
```shell
import RPi.GPIO as GPIO
import time

GPIO.setmode(GPIO.BCM)
GPIO.setwarnings(False)
GPIO.setup(18,GPIO.OUT)
print "LED on"
GPIO.output(18,GPIO.HIGH)
time.sleep(3)
print "LED off"
GPIO.output(18,GPIO.LOW)
```
https://cloud.githubusercontent.com/assets/28270453/25677336/95483dd6-3013-11e7-9ce2-9d105d02d8c6.png
