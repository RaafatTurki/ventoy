# Ventoy

### Usage
intall [ventoy](https://www.ventoy.net/en/index.html) on a usb drive then clone this within that.

your folder structure should look like so:
```sh
persistence/            # used to store persisting images across boots
ventoy/                 # this repo

image_1.iso             # all .iso images go here
image_2.iso
.
.
```

* if ventoy GUI is acting sluggish due to limited resources press `F7` to switch to text mode

### Development
you can't edit ventoy while booting from it so use this to edit the main config file
```sh
cd /run/media/$USER/Ventoy/ventoy && nvim ventoy.json && cd ~
```

and this to boot it with qemu (`/dev/sde` is assumed to be the usb drive block device)
- qemu
- udiskie
- [devour](https://github.com/salman-abedin/devour) (optional)
```sh
umount /dev/sde1 && udiskie -m /dev/sde1 & _ devour qemu-system-x86_64 -hdb /dev/sde
```

### References
- https://www.ventoy.net/en/plugin_theme.html
- http://wiki.rosalab.ru/en/index.php/Grub2_theme_tutorial

### TODO
- add in a UEFI qemu setup
