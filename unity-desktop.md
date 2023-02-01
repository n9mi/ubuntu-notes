## Install dbus-x11
```
sudo apt-get install dbus-x11
```

## Install regular unity dekstop
```
sudo apt-get update
sudo apt install ubuntu-unity-desktop
```
Configure the lightdm and please choose the lightdm display manager over gdm3. Then reboot the machine.

## If your're using laptop with touchpad, by default the touch-by-click touchpad feature isn't enabled. Install this to make the touchpad working normally.
```
sudo apt-get install xserver-xorg-input-synaptics
```
