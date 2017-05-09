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
