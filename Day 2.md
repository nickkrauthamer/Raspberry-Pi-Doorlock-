# Turn on LED via Raspberry Pi 3
Connect LED to breadboard using two jumper cables to pin 6 and 12 on the pi

Use 330 ohm resistor to limit the current flow

Script
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
