# Waveshare-PoE-HAT-B-Ubuntu

Specifically for this PoE-HAT: https://www.waveshare.com/wiki/PoE_HAT_(B)

This is a result of adaptation of https://github.com/grootwitbaas/Waveshare-PoE-HAT-B-Home-Assistant-Addon to OpenWRT distro.

It works on Raspberry Pi 4B 64-bit with Ubuntu 64.

## Install ##

1. apt update
2. apt install gcc python3-dev python3-numpy  python3-smbus python3-libgpiod libbcm2835-dev
3. pip install RPi.GPIO
4. git clone https://github.com/gianlucagiacometti/Waveshare-PoE-HAT-B-Ubuntu.git
5. copy /bin /lib /cfg into /opt

## Test ##

Use the command
```
python3 /opt/bin/main.py &
```

## Start at boot ##

insert in rc.local
```
python3 /opt/bin/main.py &
```

or 

create an systemd service according to Ubuntu standards
