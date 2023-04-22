retroflag-gpi-case
==================
System files for Raspberry Pi OS to relay the GPIO connections.

- Before editing the remote boot loader, create on the remote side a backup of `/boot/config.txt` and `/boot/overlays/dpi24.dtbo`:
  ``` Shell
  sudo cp /boot/config.txt /boot/config.original
  sudo cp /boot/overlays/dpi24.dtbo /boot/overlays/dpi24.original
  ```

- Upload system files in your terminal app with the `scp` command to the remote home folder.
  ``` Shell
  scp boot/config.txt pi@raspberrypi.local:/home/pi/config.txt
  scp boot/overlays/dpi24.dtbo pi@raspberrypi.local:/home/pi/dpi24.dtbo
  scp boot/overlays/pwm-audio-pi-zero.dtbo pi@raspberrypi.local:/home/pi/pwm-audio-pi-zero.dtbo
  ```

- While removing unecessary packages from the default installation, be aware that the `avahi-daemon` package is responsible for access to the Raspberry PI via its hostname `raspberrypi.local`.
  Otherwise you have to use an IP address for SCP and SSH, f.eks. `pi@192.168.0.3` instead of `pi@raspberrypi.local`.
