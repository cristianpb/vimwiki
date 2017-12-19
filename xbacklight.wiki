# xbackligth 

- Add to the file `/etc/default/grub` : `GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi= acpi_backlight=intel"`
- Regenerate grub file with `sudo grub-mkconfig -o /boot/grub/grub.cfg`
- In order to brightness to obtain the goo backlight, add a `*.conf` file to the folder `/etc/X11/xorg.conf.d/` with:
```
Section "Device"
    Identifier  "Card0"
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection
```
