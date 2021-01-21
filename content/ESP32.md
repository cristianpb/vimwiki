# Pin definition 

https://randomnerdtutorials.com/esp32-cam-camera-pin-gpios/#board6


## ESP EYE 

```cpp
#define PWDN_GPIO_NUM    -1
#define RESET_GPIO_NUM   -1
#define XCLK_GPIO_NUM    4
#define SIOD_GPIO_NUM    18
#define SIOC_GPIO_NUM    23
#define Y9_GPIO_NUM      36
#define Y8_GPIO_NUM      37
#define Y7_GPIO_NUM      38
#define Y6_GPIO_NUM      39
#define Y5_GPIO_NUM      35
#define Y4_GPIO_NUM      14
#define Y3_GPIO_NUM      13
#define Y2_GPIO_NUM      34
#define VSYNC_GPIO_NUM   5
#define HREF_GPIO_NUM    27
#define PCLK_GPIO_NUM    25
```

Web server

https://randomnerdtutorials.com/esp32-cam-take-photo-display-web-server/

arduino board url

https://dl.espressif.com/dl/package_esp32_index.json


# Flash 

esptool.py --chip esp32 --port /dev/ttyUSB0 --baud 460800 write_flash -z 0x1000 micropython_b7883ce_esp32_idf4.x_ble_camera.bin


```
B0 --baud 460800 write_flash -z 0x1000 micropython_b7883ce_esp32_idf4.x_ble_camera.b

n
esptool.py v2.8
Serial port /dev/ttyUSB0
Connecting....
Chip is ESP32D0WDQ5 (revision 1)
Features: WiFi, BT, Dual Core, 240MHz, VRef calibration in efuse, Coding Scheme None
Crystal is 40MHz
MAC: bc:dd:c2:d0:24:74
Uploading stub...
Running stub...
Stub running...
Changing baud rate to 460800
Changed.
Configuring flash size...
Auto-detected Flash size: 4MB
Compressed 1567824 bytes to 982369...
Wrote 1567824 bytes (982369 compressed) at 0x00001000 in 22.6 seconds (effective 554

7 kbit/s)...
Hash of data verified.

Leaving...
Hard resetting via RTS pin...
```
