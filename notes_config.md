# titlebar, headerbar
gsettings set org.gnome.Terminal.Legacy.Settings headerbar false

gsettings set org.gnome.Terminal.Legacy.Settings default-show-menubar false

https://askubuntu.com/questions/821813/how-to-slim-down-ubuntu-gnome-title-bar-fatness
~/.config/gtk-3.0/gtk.css


# TLP for power, battery life improvements
https://tipsonubuntu.com/2018/11/18/quick-tip-improve-battery-life-ubuntu-18-04-higher/

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

