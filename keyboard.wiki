## Keyboard language


Add `/etc/X11/xorg.conf.d/00-keyboard.conf`

```
Section "InputClass"
        Identifier "system-keyboard"
        MatchIsKeyboard "on"
        Option "XkbLayout" "fr"
EndSection
```
