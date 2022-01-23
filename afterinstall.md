# Connect to internet
```
# cp /etc/wpa_supplicant/wpa_supplicant.conf /etc/wpa_supplicant/wpa_supplicant-wlp2s0.conf

# wpa_passphrase "Redmi 5A" "192168430" >> /etc/wpa_supplicant/wpa_supplicant-wlp2s0.conf

# wpa_supplicant -D wext -i wlp2s0 -c /etc/wpa_supplicant/wpa_supplicant-wlp2s0.conf &

# ip a
```
# Install window manager (spectrwm)
```
# xbps-install -S

# xbps-install -u

# xbps-install xorg terminator dbus spectrwm chromium
```
# Configure spectrwm
```
$ xbps-query -f spectrwm
$ mkdir .config/spectrwm
$ cp /usr/etc/spectrwm.conf .config/spectrwm/
$ cp /usr/share/doc/spectrwm/examples/baraction.sh .config/spectrwm/
$ cp /usr/share/doc/spectrwm/examples/screenshot.sh .config/spectrwm/
$ cp /usr/share/doc/spectrwm/examples/spectrwm_us.conf .config/spectrwm/
$ chmod +x .config/spectrwm/screenshot.sh
$ sudo xbps-install vim neofetch git scrot
$ vim .config/spectrwm/spectrwm.conf
```
# Configure terminator
```
- disable show scrollbar
- disable show titlebar
- enable copy on selection
- background transparan
- infinite scrollback
```

# install firmware
```
$ sudo xbps-install void-repo-nonfree
$ sudo xbps-install void-repo-multilib
$ sudo xbps-install void-repo-multilib-nonfree
$ sudo xbps-install -S
$ sudo xbps-install intel-ucode
```
# Enabling locale
```
$ sudo vim /etc/default/libc-locales
```
uncomment `en_US.UTF-8`
# Setting system locale
```
Set LANG="en_US.UTF-8" in /etc/locale.conf
```
# Set root shell to bash
```
$ sudo chsh -s /usr/bin/bash root
```
# Run dbus
```
$ sudo ln -s /etc/sv/dbus /var/service
```
# Basic runit
```
# sv up <services>

# sv down <services>

# sv restart <services>

# sv status <services>

# sv status dhcpcd

# sv status /var/service/*

Enable service

# ln -s /etc/sv/<service> /var/service/

If the system is not currently running, the service can be linked directly into the default runsvdir

# ln -s /etc/sv/<service> /etc/runit/runsvdir/default/

Disable service

# rm /var/service/<service>
# rm /etc/runit/runsvdir/default/<service>

Testing Services
To check if a service is working correctly when started by the service supervisor, run it once before fully enabling it:

# touch /etc/sv/<service>/down
# ln -s /etc/sv/<service> /var/service/
# sv once <service>
```
# log
```
$ sudo xbps-install socklog-void
$ sudo ln -s /etc/sv/socklog-unix/ /var/service
$ sudo ln -s /etc/sv/nanoklogd/ /var/service
```
```
$ sudo svlogtail
```
# configuration
```
/etc/rc.conf
```
# fstrim for ssd
```
# vim /etc/fstab
```
```
UUID=3dffe232-c52a-42c2-b894-cb8c97dcd593 / ext4 defaults,discard 0 1
```
# Security
```
# xbps-install apparmor
# vim /etc/default/grub
```
```
GRUB_CMDLINE_LINUX_DEFAULT="loglevel=4 apparmor=1 security=apparmor"
```
```
# update-grub
```
# power saving
```
# xbps-install tlp
# ln -s /etc/sv/tlp/ /var/service
```
# install networkmanager
```
# xbps-install NetworkManager network-manager-applet
```
disable wps_supplicant and dhcpd
```
# rm /run/wpa_supplicant/wlp2s0
# rm /var/service/dhcpd
```
enable NetworkManager
```
# ln -s /etc/sv/NetworkManager/ /var/service
```
```
# reboot
```
```
# nmcli d wifi list
# nmcli d wifi connect "KGS Connect Pa 2"
```
or 
```
nmtui
```
# thumbnailpreview
```
$ sudo xbps-install ffmpegthumbs
```
# Audio
```
$ sudo xbps-install -S pulseaudio alsa-plugins-pulseaudio
$ sudo ln -s /etc/sv/pulseaudio/ /var/service
```
# vpsm
```
$ sudo xbps-install vpsm
$ git clone https://github.com/void-linux/void-packages.git
```
```
$ vim .bashrc
```
```
export XBPS_DISTDIR=/home/malik/Packages/void-packages
```
```
$ vpsm -i 
$ vpsm ss
$ vpsm un
$ vpsm upr
$ vpsm bu
```
