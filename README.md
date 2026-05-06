# Waveshare-PoE-HAT-B-Ubuntu

Specifically for this PoE-HAT: https://www.waveshare.com/wiki/PoE_HAT_(B)

This is a result of adaptation of https://github.com/grootwitbaas/Waveshare-PoE-HAT-B-Home-Assistant-Addon to OpenWRT distro.

It works on Raspberry Pi 4B 64-bit with Ubuntu 64.

## Install on 26.04 ##

1. apt update
2. apt install gcc python3-dev python3-numpy  python3-smbus python3-libgpiod libbcm2835-dev python3-rpi.gpio python3-pil
3. git clone https://github.com/gianlucagiacometti/Waveshare-PoE-HAT-B-Ubuntu.git
4. copy /bin /lib /cfg into /opt

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

insert in /etc/systemd/system/poe-hat-b.service

```
[Unit]
Description=PoE HAT (B) OLED
After=network.target

[Service]
ExecStart=/usr/bin/python3 /opt/bin/main.py
WorkingDirectory=/opt/bin
StandardOutput=journal
StandardError=journal
Restart=always

[Install]
WantedBy=multi-user.target
```

then run

systemctl daemon-reload
systemctl enable poe-hat-b
