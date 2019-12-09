## Configure using libinput

Add `/etc/X11/xorg.conf.d/30-touchpad.conf`:

```conf
Section "InputClass"
    Identifier "touchpad"
    Driver "libinput"
    MatchIsTouchpad "on"
    Option "Tapping" "on"
    Option "TappingButtonMap" "lmr"
EndSection
```
