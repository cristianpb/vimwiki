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
