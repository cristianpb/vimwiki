## Flash

```
./venv/bin/python TinyFPGA-Programmer-Application/tinyfpga-programmer-gui.py --port /dev/ttyACM0 --mode --m4app quickfeather-data-collection.bin
CLI mode
ports =  ['/dev/ttyACM0 (QuickFeather)'] 1
Using port  /dev/ttyACM0 (QuickFeather)
Programming m4 application with  quickfeather-data-collection.bin
Erasing designated flash pages
Erase  64.0 KiB ( 0xd8 ) at  0x80000
Erase  64.0 KiB ( 0xd8 ) at  0x90000
Erase  32.0 KiB ( 0x52 ) at  0xa0000
Erase  4.0 KiB ( 0x20 ) at  0xa8000
Erase  4.0 KiB ( 0x20 ) at  0xa9000
Erase  4.0 KiB ( 0x20 ) at  0xaa000
Erase  4.0 KiB ( 0x20 ) at  0xab000
Erase  4.0 KiB ( 0x20 ) at  0xac000
Erase  4.0 KiB ( 0x20 ) at  0xad000
Erase  4.0 KiB ( 0x20 ) at  0xae000
Erase  4.0 KiB ( 0x20 ) at  0xaf000
Writing  binary
Write  193176  bytes
[XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX]
Verifying  binary
FastREAD 0x0B ( 193176 )
[XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX]
Success: read_back == data
Writing metadata
Erasing designated flash pages
Erase  4.0 KiB ( 0x20 ) at  0x13000
Writing  metadata
Write  8  bytes
[X]                                               ]
Verifying  metadata
FastREAD 0x0B ( 8 )
[X]                                               ]
Success: read_back == data
mode: []
```

## Reading hello world


```sh
screen /dev/ttyUSB0 115200
```

Output:

```
##########################
Quicklogic QuickFeather Bootloader
SW Version: qorc-sdk/qf-apps/qf_bootloader(v2) (GCC)
Jun  7 2020 11:50:58
##########################

User button not pressed: proceeding to load application


##########################
Quicklogic QuickFeather MQTT-SN/SensiML Interface Example
SW Version: C Jun-2020
Jul 31 2020 11:05:53
##########################



Hello world!!

Sample rate: 400
Sample resolution : 6
Sample range      : 0
Sample rate       : 400
Datablock processor task name: DBP_IMU_THREAD
inQ         : 0x2004c550
#*******************
Command Line Interface
App SW Version: C Jun-2020
#*******************
```


search for quickfeather on github:
https://antmicro.com/blog/2020/03/quickfeather-release/
https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/zephyr/boards/arm/warp7_m4/doc/index.html
https://www.hackworkplay.com/2021/01/19/the-quickfeather-dev-kit-has-arrived/

zephry 
https://docs.zephyrproject.org/latest/samples/hello_world/README.html#hello-world
quick start
https://sensiml.com/documentation/firmware/quicklogic-quickfeather/quicklogic-quickfeather.html#flashing-quickfeather-firmware
more complicated example
https://github.com/QuickLogic-Corp/qorc-sdk/tree/master/qf_apps/qf_ssi_ai_app

hackser example
https://www.hackster.io/gatoninja236/getting-started-with-the-quickfeather-dev-kit-and-sensiml-9881a3
connecting cables
https://www.hackster.io/PSoC_Rocks/programming-quickfeather-in-zephyr-linux-4610cc

## compiling
          
```
make TC_PATH=/usr/bin
```

./venv/bin/python TinyFPGA-Programmer-Application/tinyfpga-programmer-gui.py --port /dev/ttyACM0 --mode --m4app qf_ssi_ai_appRecog.bin

          
```
screen /dev/ttyUSB0 460800
```

## water flow sensor

funcionamiento
https://www.seeedstudio.com/blog/2020/05/11/how-to-use-water-flow-sensor-with-arduino/

wiring 
https://www.instructables.com/How-to-Use-Water-Flow-Sensor-Arduino-Tutorial/
