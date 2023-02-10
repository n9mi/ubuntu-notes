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

## Enabling touchpad 
If your're using laptop with touchpad, at some cases the touch-by-click touchpad feature isn't enabled. Install this to make the touchpad working normally.
```
sudo apt-get install xserver-xorg-input-synaptics
```

## Add nemo as default file manager
```
xdg-mime default nemo.desktop inode/directory
```
