# titlebar, headerbar
gsettings set org.gnome.Terminal.Legacy.Settings headerbar false

gsettings set org.gnome.Terminal.Legacy.Settings default-show-menubar false

https://askubuntu.com/questions/821813/how-to-slim-down-ubuntu-gnome-title-bar-fatness
~/.config/gtk-3.0/gtk.css


# TLP for power, battery life improvements
https://tipsonubuntu.com/2018/11/18/quick-tip-improve-battery-life-ubuntu-18-04-higher/
sudo apt-get install tlp
sudo add-apt-repository ppa:linuxuprising/apps
sudo apt-get install tlpui


# mouse triple click
synclient TapButton3=2

dconf editor middle click emulation

# dconf edditor mutter
org/gnome/mutter
  setting auto-maximize   set slider to off


# trackpad scrolling
xinput list-props 10 | grep Scroll
Synaptics Scrolling Distance (286):	27, 27

xinput set-prop 10 286 50, 50

# ubunutu windows time difference
http://ubuntuhandbook.org/index.php/2016/05/time-differences-ubuntu-1604-windows-10/

 Disable UTC and use Local Time in Ubuntu:
timedatectl set-local-rtc 1 --adjust-system-clock


# blue tooth disable
https://askubuntu.com/questions/67758/how-can-i-deactivate-bluetooth-on-system-startup

in /etc/bluetooth/main.conf
AutoEnable=false

sudo systemctl disable bluetooth.service

# sensors scan,  sudo sensors-detect
https://askubuntu.com/questions/22108/how-to-control-fan-speed

Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK
---> got error that no pwm sensors were available


# dell apt for fans
https://askubuntu.com/questions/281478/fan-speed-in-ubuntu-pwmconfig-no-pwm-capable-sensor-modules-installed


# remove xubuntu desktop, lightdm, and xfce4 packages
https://www.hiroom2.com/2017/11/23/ubuntu-1710-xfce-en/

night light worked better on Gnome

# install xfce4 on ubuntu.  the alt+tab window border was nice to have.
https://linuxconfig.org/install-xfce-desktop-on-ubuntu-18-04-bionic-beaver-linux
sudo apt-get install xfce4-desktop

  then try building flux like i have on the debian computer
https://github.com/xflux-gui/fluxgui
sudo add-apt-repository ppa:nathan-renniewaldock/flux
sudo apt-get update
sudo apt-get install fluxgui


# power manager and brightness control
https://docs.xfce.org/xfce/xfce4-power-manager/brightness



# firefox address bar search suggestions
https://www.reddit.com/r/FirefoxCSS/comments/fyi6tl/remove_search_with_and_visit_from_url_menu_in_ff75/

https://www.userchrome.org/megabar-styling-firefox-address-bar.html

- note: about:config custom style sheet has to be enabled (it's disabled by default)

# partition from ubuntu 19 was unmounted
https://askubuntu.com/questions/1029040/how-to-manually-mount-a-partition
https://askubuntu.com/questions/409205/how-to-extend-partition-with-free-space-that-is-before-it-using-gparted

svyat@XPS-7390:~$ lsblk -o NAME,FSTYPE,LABEL,SIZE,MOUNTPOINT
NAME        FSTYPE    LABEL         SIZE MOUNTPOINT
loop0       squashfs                 55M /snap/core18/1705
loop1       squashfs              240.8M /snap/gnome-3-34-1804/24
loop2       squashfs              255.6M /snap/gnome-3-34-1804/36
loop3       squashfs                 55M /snap/core18/1880
loop4       squashfs               49.8M /snap/snap-store/467
loop5       squashfs               49.8M /snap/snap-store/433
loop6       squashfs               29.9M /snap/snapd/8542
loop7       squashfs               27.1M /snap/snapd/7264
loop8       squashfs               62.1M /snap/gtk-common-themes/1506
nvme0n1                           238.5G
├─nvme0n1p1 vfat      ESP           650M /boot/efi
├─nvme0n1p2                         128M
├─nvme0n1p3 BitLocker             167.2G
├─nvme0n1p4 ntfs      WINRETOOLS    990M
├─nvme0n1p5 ntfs      Image         9.5G
├─nvme0n1p6 ntfs      DELLSUPPORT   1.5G
├─nvme0n1p7 ext4                     14G /
├─nvme0n1p8 swap                    7.5G
└─nvme0n1p9 ext4                   37.2G

svyat@XPS-7390:~$ sudo mkdir /mnt/ubu_19

svyat@XPS-7390:~$ ls /mnt/
ubu_19

svyat@XPS-7390:~$ sudo mount -t auto -v /dev/nvme0n1p9 /mnt/ubu_19
mount: /dev/nvme0n1p9 mounted on /mnt/ubu_19.

