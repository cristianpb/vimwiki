# Samba configuration

## smb.conf

configuration

```conf
[RaspiMovShare]
comment=RaspiMov Share
path=/home/pi/Images
browseable=Yes
writeable=Yes
only guest=no
create mask=0777
directory mask=0777
public=no
```

##. Setting up User Accounts and Connecting to Share

sudo smbpasswd -a username
