Source : https://www.hifiberry.com/build/documentation/configuring-linux-3-18-x/

# Disable default sound conf + add DAC conf
SSH to the raspberry pi

sudo vi /boot/config.txt

Comment this line at the end of the file :
dtparam=audio=on
And add this line :
dtoverlay=hifiberry-dac

# Create asound config file

sudo vi /etc/asound.conf

```
pcm.!default {
  type hw card 0
}
ctl.!default {
  type hw card 0
}
```
