# E-mail pohotos from motion detection
```shell
sudo apt-get update
sudo apt-get install motion postfix heirloom-mailx
```
After postfix adds default options select "internet site with smart host"
```shell
sudo nano etc/postfix/main.cf
```
Add/Change the file name to include 
```shell
relayhost = [smtp.gmail.com]:587
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/postfix/cacert.pem
smtp_use_tls = yes
```
```shell
sudo nano etc/postfix/sasl_passwd
```
Next enter “[smtp.gmail.com]:587 username@gmail.com:password” with your username and password, exlcuding the quotations. 
```shell
sudo postmap /etc/postfix/sasl_passwd
sudo chown postfix /etc/postfix/sasl_passwd
sudo chmod 400 /etc/postfix/sasl_passwd
```
Next validate certificates to avoid any errors
```shell
cat /etc/ssl/certs/Thawte_Premium_Server_CA.pem | sudo tee -a /etc/postfix/cacert.pem
```
Reload postfix
```shell
/etc/init.d/postfix reload
```
Test to see if everything is working properly by entering
```shell
echo "This is a test." | mail -s "Testing 1 2 3" (email address here)@gmail.com
```
Finishing up with motion
```shell
sudo nano /etc/default/motion
```
change  “start_motion_daemon=no” to  “start_motion_daemon=yes”
```shell
sudo nano /etc/motion/motion.conf
```
Daemon = OFF to ON
webcam_localhost = ON to OFF

In order to have the software email photos of movement, uncomment and edit the "on picture save line"
```shell
sudo service motion start
```
