# Setup Live Stream Webcam
## Make sure updates are installed
```shell
sudo apt-get update
sudo apt-get upgrde
```
## Instal motion service
```shell
sudo apt-getinstall motion...
```
## Configuring software
```shell
sudo nano /etc/motion/motion.conf
```
```shell
DAEMON = ON
Webcam_localhost = OFF
IPV6_ON
Webcontrol_localhost = OFF
output_pictures off
ffmpeg output_movies off
stream_maxrate 100
framerate_100
```
### Enabling the DAEMON service
```shell
sudo nano /etc/default/motion
start_motion_daemon = yes
```
### To start and stop the motion service
```shell 
sudo service motion start
sudo service motion stop
