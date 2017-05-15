# Installing open CV
Go to link 
http://www.pyimagesearch.com/2016/04/18/install-guide-raspberry-pi-3-raspbian-jessie-opencv-3
Install guide: Raspberry Pi 3 + Raspbian jessie + Open CV
```shell
sudo raspi-config
```
REBOOT
```shell
sudo reboot
```
Raspberry Pi 3 + Raspbian Jessie + Open CV
```shell
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root       7.2G  3.3G  3.6G  48% /
devtmpfs        459M     0  459M   0% /dev
tmpfs           463M     0  463M   0% /dev/shm
tmpfs           463M  6.4M  457M   2% /run
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           463M     0  463M   0% /sys/fs/cgroup
/dev/mmcblk0p1   60M   20M   41M  34% /boot
tmpfs            93M     0   93M   0% /run/user/1000
```
Raspberry Pi 3 + Raspbian jessie + Open CV
```shell
sudo apt-get purge wolfram-engine
```
## Install Dependencies 
Update and Upgrade any existing packages
```shell
sudo apt-get update
sudo apt-get upgrade
```
Install developer tools including CMake
```shell
sudo apt-get install build essential cmake pkg-config
```
Install image I/O packages to load various image file formats from disk
```shell
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
```
Install video I/O packages to read various video file/formats from disk and streams
```shell
sudo apt-get install libavcodec-dev libavformat-dev libwscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
```
Install GTK develpomental library
```shell
sudo apt-get install libgtk2.0-dev
```
Optimize operations of OpenCV and dependecies
```shell
sudo apt-get install libatlas-base-dev gfortran
```
Install both Python 2.7 and Python 3 header files so we can compile Open CV with python bindings
```shell
sudo apt-get install python2.7-dev python3-dev
```
## Download OpenCV source code
Get the 3.1.0 archive of OpenCV fron the official OpenCV Repository
```shell
cd ~
wget -O opencv.zip https://github.com/Itseez/open/archive/3.1.0.zip
unzip opencv.zip
```
To get full install of OpenCV, get the opencv_contrib repository 
```shell
wget -O opencv_contrib.zip https://github.com/itseez/opencv_contrib/archive/3.1.0.zip
unzip opencv_contrib.zip
```
## install pop ( a Python package manager)
```shell
wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py
```
Install virtual environments 
```shell
sudo pip install virtualenvwrapper
sudo rm -rf ~/.cache/pip
```
Update ~/.profile file to include the following lines at the bottom of the file
```shell
virtualenv and virtualenvwrapper
export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
```
Use cat and output redirection to handle updating ~/.profile
```shell
echo -e "\n# virtualenv and virtualenvwrapper" >>~/.profile
echo "export WORKON_HOME=$HOME/.virtualenvs >> ~/.profile
echo "source /usr/local/nin/virtualenvwrapper.sh" >> ~/.profile
```
Reload ~/.profile to make sure changes take affect by logging out and then logging back in or using the source command.
## Creating your Python virtual environment (For Python 2.7)
```shell
mkvirtualenv cv -p python2
```
Use workon to drop down into your virtual environment
```shell
source ~/.profile
workon cv
```
To make sure you are in the cv virtual environment check your command line and see if there is a (cv) text prompt, if there is then you are in the cv virtual environment
## Installing NumPy on Raspberry Pi
```shell
pip instll numpy
```
## Compile and Instal OpenCV
Setup our build using CMake
```shell
cd ~/opencv-3.1.0/
mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib-3.1.0/modules \
    -D BUILD_EXAMPLES=ON ..
```
    
