# Setting up Raspberry Pi using Blynk Smartphone App
## Wiring Pi
### Install Wiring Pi
Wiring Pi is used to switch the GPIO pins high and low.
#### Download instructions
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

Create a file 
```shell
nano LED.py
```
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
Reference wiring image
https://cloud.githubusercontent.com/assets/28270453/25677336/95483dd6-3013-11e7-9ce2-9d105d02d8c6.png

## Download Blynk 
download blynk library at https://github.com/blynkkk/blynk-library.git
```shell
cd blynk-library linux
```
make clean all target=raspberry

## Run Blynk
```shell
sudo ./blynk --token=YourAuthToken
```
## Connecting Raspberry Pi to blink
Connect Raspbery Pi to the Internet and open console, then run the following command that updates your IS package repository
```shell
curl -sL "https://deb.nodesource.com/setup_6.x" | sudo -E bash -
```
Download and build Blynk JS library using npm
```shell
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential
sudo npm install -g npm
sudo npm install -g onoff
sudo npm install -g blynk-library
```
Run Blynk test script (put your auth token);
```shell
blynk-client 715f8cafe95f4a91bae319d0376caa8c
```
You can write your own script based on https://github.com/vshymanskyy/blynk-library-js/tree/master/examples
#### To enable Blynk auto restart for Pi, find /etc/rc.local file and add "node full_path_to_your_script.js <Auto Toekn>
