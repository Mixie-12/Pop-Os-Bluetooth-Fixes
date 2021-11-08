# Pop-Os-general-Fixes
Things to do before 


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

## Pop-Os-general-Fixes
