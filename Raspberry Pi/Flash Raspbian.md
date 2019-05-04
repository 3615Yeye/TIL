# Format sd card as a fat device
Using gnome disk for example.

# Find microsd device name
sudo fdisk -l

# Flash 
sudo dd if=imgFile of=/dev/deviceName bs=4M

Ex : sudo dd if=2019-04-08-raspbian-stretch-lite.img of=/dev/mmcblk0 bs=4M

# Headless SSH server
To connect directly in SSH to the RPi without pluging a screen, keyboard...

Create an empty ssh file in /boot partition :
cd /path/to/microsdcard/boot
touch ssh

# Headless connection to wifi
Same as above but in wpa_supplicant.conf file

cd /path/to/microsdcard/boot
vim wpa_supplicant.conf

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=FR

network={
	ssid="Wifi name"
	psk="Wifi password"
	key_mgmt=WPA-PSK
}
```

# Find your Raspberry ip
