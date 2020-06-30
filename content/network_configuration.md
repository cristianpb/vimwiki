## Change interface name

Note: When changing the naming scheme, do not forget to update all network-related configuration files and custom systemd unit files to reflect the change.

You can change the device name by defining the name manually with an udev-rule. For example:

* /etc/udev/rules.d/10-network.rules
 
```conf
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="aa:bb:cc:dd:ee:ff", NAME="net1"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="ff:ee:dd:cc:bb:aa", NAME="net0" 
```
