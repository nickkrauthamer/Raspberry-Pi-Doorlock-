# Installing Smartphone-Doorlock
## Installing node.js library
Following code is to remove old versions of node.js
```shell
sudo apt-get purge node nodejs node.js-y
sudo apt-get autoremove
```
Automatic node.js installation
```shell
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash - 
```
```shell
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential nodejs -y
```
## Installing Smarphone Doorlock
```shell
git clone https://github.com/HackerHouseYT/Smartphone-Doorlock.git
```
```shell
cd Smartphone-Doorlock/
```
```shell
sudo npm install
```
If using lite version of raspian jessie, do the following- 
``shell
wget abysz.co.uk/rpi/pigpio/pigpio.zip
unzip pigpio.zip
make
sudo make install
```
go to
```shell
cd Smartphone-Doorlock
```
```shell
npm install pigpio
```
Enter authentication code from Blynk app via 
```shell
sudo nano doorlock.js
```
To start doorlock program
```shell
sudo node doorlock.js
```
