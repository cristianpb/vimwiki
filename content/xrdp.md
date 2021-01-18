# No keyboard or mouse when connected via xorg

The fix for me was to add Option "CoreKeyboard" and Option "CorePointer" to the inputdevices in /etc/X11/xrdp/xorg.conf since the inputdevices in the serverlayout section are apparently ignored so no core pointer and keyboard exists, which leads to forced default devices. No idea why this is suddenly the case, it worked fine on ubuntu 18.04, but broke for me in 20.04.

```conf
Section "InputDevice"
    Identifier "xrdpKeyboard"
    Driver "xrdpkeyb"
    Option "CoreKeyboard"
EndSection

Section "InputDevice"
    Identifier "xrdpMouse"
    Driver "xrdpmouse"
    Option "CorePointer"
EndSection
```

https://github.com/neutrinolabs/xorgxrdp/issues/164
