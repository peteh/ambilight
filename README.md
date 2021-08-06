# ambilight
Ambilight setup for my TV


# PI Zero W Modifications

## /boot/config.txt Changes
### Set IOs for POWER ON/OFF Led and Relay switch

```
# Pete: used to allow shutdown on gpio pin 5
dtoverlay=gpio-shutdown
# Pete: enable gpio 24 at boot
#  23: power led
#  24: relais for power for fan and ledstrip
gpio=23=op,dh 
gpio=24=op,dh 
```

### disable Audio
```
# Pete: disable audio
dtparam=audio=off
```


### Allow boot up and shutdown via IO
```
# Pete: used to allow shutdown on gpio 3
dtoverlay=gpio-shutdown
```

### Hyperiond Service user
To allow hyperion to access IOs, I set the service to run as root user. (There might be a better solution, but I could not find one)

```
sudo systemctl disable --now hyperiond@pi
sudo systemctl enable --now hyperiond@root
```


# Hyperion Configuration
## LED Layout
Top: 90

Left/Right: 50

Bottom: 93

Total: 283

## LED Configuration
### Main LedStrip
Max Led: 290

GPIO: 18

DMA: 5

PWM: 0

### Secondary Ledstrip
(So far not working)

GPIO: 13

DMA: 10

PWM: 1

## HDMI Capture Configuration
Device: USB Video

Input: Automatic

Resolution: 640x480

FPS: 60

Size Decimation: 4
