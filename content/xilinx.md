# Xilinx notes

## ressources

* https://forums.xilinx.com/t5/Adaptive-Computing-Challenge/bd-p/ACC_2020
* machine learning tutorial: https://github.com/Xilinx/Vitis-In-Depth-Tutorial/blob/master/Machine_Learning/Introduction/README.md
* VART, compile pretrained models https://github.com/Xilinx/Vitis-AI/tree/master/VART
* gstereamer for read video https://www.e-consystems.com/blog/camera/getting-started-with-xilinx-zynq-ultrascale-mpsoc-zcu104-evaluation-kit-and-see3cam_cu30_chl_tc_bx/
* vitis ai docuementation https://china.xilinx.com/html_docs/vitis_ai/1_2/setupevaluationboard.html#yjf1570690235238
 

## config

zynq image doesn't not have configuration for usb0 internet connection
so you can either do a temp config

### temp configuration

* usb modem up
 
 ```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qle
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
3: can0: <NOARP,ECHO> mtu 16 qdisc noop state DOWN group default qlen 10
    link/can
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default q
    link/ether 00:0a:35:05:63:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.99/24 brd 192.168.2.255 scope global eth0:1
       valid_lft forever preferred_lft forever
    inet6 fe80::20a:35ff:fe05:6347/64 scope link
       valid_lft forever preferred_lft forever
6: usb0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e6:2e:a6:96:38:21 brd ff:ff:ff:ff:ff:ff
```


```bash
 sudo ifconfig usb0 up
```

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qle
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
3: can0: <NOARP,ECHO> mtu 16 qdisc noop state DOWN group default qlen 10
    link/can
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default q
    link/ether 00:0a:35:05:63:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.99/24 brd 192.168.2.255 scope global eth0:1
       valid_lft forever preferred_lft forever
    inet6 fe80::20a:35ff:fe05:6347/64 scope link
       valid_lft forever preferred_lft forever
6: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN gr
    link/ether e6:2e:a6:96:38:21 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::e42e:a6ff:fe96:3821/64 scope link
       valid_lft forever preferred_lft forever
```


```bash
sudo dhclient usb0
```

```
xilinx@pynq:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qle
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: sit0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1000
    link/sit 0.0.0.0 brd 0.0.0.0
3: can0: <NOARP,ECHO> mtu 16 qdisc noop state DOWN group default qlen 10
    link/can
4: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default q
    link/ether 00:0a:35:05:63:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.99/24 brd 192.168.2.255 scope global eth0:1
       valid_lft forever preferred_lft forever
    inet6 fe80::20a:35ff:fe05:6347/64 scope link
       valid_lft forever preferred_lft forever
6: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN gr
    link/ether e6:2e:a6:96:38:21 brd ff:ff:ff:ff:ff:ff
    inet 192.168.42.253/24 brd 192.168.42.255 scope global usb0
       valid_lft forever preferred_lft forever
    inet6 fe80::e42e:a6ff:fe96:3821/64 scope link
       valid_lft forever preferred_lft forever
```

### Permanent config

```config
#/etc/network/interfaces.d/usb0

auto usb0
iface usb0 inet dhcp
```
