# Changing Multichannel Voice Intput into Mono
### Go to voice Command folder in PiAUISuite
### Edit speechrecognition.sh as @ripleyXLR8 mentioned above (essentially change "-f cd -t wav" to "-f S16_LE")
### Edit voice command.cpp as @ripleyXLR8 mentioned above
```shell
sudo apt-get install g++-4.8
```
### Make
### Go to install folder 
```shell
sudo ./INstallAUISuite.sh
```
### Change the keyword in configuration to something else because "Pi" can be confused with "pie"
### Config file for for PiAUISuite should look like
```shell
#This is the default config file
#These are the special options you can set (remove the #)
#!verify==1
#!keyword==pi
#!thresh==0.7
#!continuous==1
#!response==Yes Sir?
#!quiet==0
#!ignore==0
#!filler==0
#!duration==2
#!com_dur==3
#!hardware==plughw:1,0
#Here are the commands
show me==/home/pi/AUI/Imaging/test 2
track me==/home/pi/AUI/Imaging/test 1
download==download ...
play $1 season $2 episode $3==playvideo -s $2 -e $3 $1
download $1 season $2 episode $3==download $1 s$2e$3
play==playvideo -r -f ...
multiple==playvideo -r -m -c 5 ...
download==download ...
YouTube==youtube-search ...
Google==google ...
~music==xterm -e pianobar
~weather==/home/pi/AUI/Misc/sayweather.sh
~made you==tts "I was created by Steven Hickson" 2>/dev/null
~music==xterm -e control-pianobar.sh play
~terminal==xterm &
~Internet==midori &
```
