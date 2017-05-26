# Voice-Activation-Raspberry-Pi
Voice activation of LED light using raspberry pi

## Flash image of raspian lite onto Raspberry Pi 3
Used etcher to flash over to Raspberry Pi 3

## Start up Raspberry Pi, go to settings using
```shell
sudo raspi-config
```
## Raspberry Pi Setup
Change user password to custom password, change timezone to US Eastern (adjust according to location)
Enable SSH and I2C
## Reboot Raspberry Pi
```shell
sudo shutdown now -r 
```
## Wifi Setup
```shell
sudo nano /etc/network/interfaces
```
Script
```shell
source-directory /etc/network/interfaces.d
sud
auto lo
iface lo inet loopback

iface eth0 inet manual

auto wlan0
allow-hotplug wlan0
iface wlan0 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf

allow-hotplug wlan1
iface wlan1 inet manual
    wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```
### Connecting to Bates Open
```shell
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```
Script
```shell
update_config=1
network={
        ssid="Bates Open"
        key_mgmt=NONE
}
```
## How to send IP address to e-mail upon boot
```shell
import smtplib
import socket
from email.MIMEMultipart import MIMEMultipart
from email.MIMEText import MIMEText

### GET IP ADDRESS
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.connect(("gmail.com",80))
ip = s.getsockname()[0]
s.close()


fromaddr = "sudoraspi3@gmail.com"
toaddr = "jlee790@yahoo.com"
msg = MIMEMultipart()
msg['From'] = fromaddr
msg['To'] = toaddr
msg['Subject'] = "SUBJECT-RASP"

body = ip
msg.attach(MIMEText(body, 'plain'))

server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
server.login(fromaddr, "ifconfig")
text = msg.as_string()
server.sendmail(fromaddr, toaddr, text)
server.quit()
```

### Boot e-mail delay
```shell
Sudo nano /etc/rc.local
 
while ! /sbin/ifconfig wlan0 | grep -q 'inet addr:[0-9]'; do
    sleep 3
done

_IP=$(hostname -I) || true
if [ "$_IP" ]; then
  printf "My IP address is %s\n" "$_IP"
  python /home/pi/sendemail.py
fi

exit 0
```
