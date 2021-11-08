# Pop-Os-general-Fixes
Things to do before using the OS.
For a user friendly distro, it sure needs some tweaking 
## Enable bluetooth stuff:
1. Edit file

sudo nano /etc/bluetooth/main.conf

Add at end: AutoEnable=true

2. Enable bluetooth startup

```
sudo systemctl enable bluetooth.service
sudo systemctl start bluetooth.service
```

3. Enable auto connect


```
git clone https://github.com/jrouleau/bluetooth-autoconnect.git

sudo cp bluetooth-autoconnect/bluetooth-autoconnect.service /etc/systemd/system/
sudo cp '/home/magnus/bluetooth-autoconnect/bluetooth-autoconnect' /usr/bin/

sudo systemctl enable bluetooth-autoconnect.service
sudo systemctl start bluetooth-autoconnect.service
```

4. Make your headset trust your computer

Run ```bluetoothctl``` and then enter 
```trust XX:XX:XX:XX:XX:XX```. Replace X'es with MAC address of your device.
You find it with ```bhcitool dev```

5. Extra bluetooth protocols
```
sudo apt-get install pulseaudio-module-bluetooth
sudo killall pulseaudio
pulseaudio --start    
sudo systemctl restart bluetooth
```
6. Adding the module-bluez5-discover at the end of the pulseaudio /etc/pulse/default.pa config:
```
load-module module-bluez5-discover
```
7. Restart PulseAudio:
```
killall pulseaudio
```
8. Add following to /etc/pulse/default.pa

```
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
load-module module-switch-on-connect # this is new!
.endif
```


