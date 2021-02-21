# Flash Xperia XZ1 compact lilac


## download stock firmware with xperia-flashtool

on linux, you can launchi it using: `mono XperiFirm.exe`

https://www.themefoxx.com/flash-stock-firmware-xperia-flashtool/

Creating FTF File from Stock Firmware

    Make sure you have downloaded the latest Xperia Flashtool.
    If the download is zipped, extract the same. Open the Flashtool.
    Go to Tools > Bundles > Create.Flash-Stock-Firmware-Xperia-Flashtool-1
    You will be asked to select a folder. Select the folder where you have downloaded the Sony Stock Firmware files from XperiFirm tool as source folder. After you select the source folder:
    1. Double click on the Device field to select the appropriate device.
    2. In the branding field, make sure you have the right name you want to be associated with your firmware.
    3. Give the appropriate version number in the Version field.


## Use newflasher to flash directly usin command line

erase extrange *.ta files and then `./newflasher.x64'

https://forum.xda-developers.com/t/tool-newflasher-xperia-command-line-flasher.3619426/

STEP 1:
- Download right firmware for your device using XperiFirm tool, put newflasher.exe into firmware dir created by XperiFirm tool. Before you double click newflasher.exe do in mind something, newflasher tool is programed to flash everything found in the same dir!!! So tool flash all .ta files, all .sin files, boot delivery (whole boot folder), partition.zip, in short all files found in dir! If you no want to flash something just move file which you no want to flash OUT OF FOLDER! Partition.zip .sin files can be flashed only if you extract partition.zip into newly created folder called partition!

STEP 2:
- To start flashing phone put your phone into flash mode, double click newflasher.exe and wait wait wait until your device gets flashed, thats it. Look into log to see if something goes wrong! If all right you are done. If not post your log so I can look!

SOME MORE THINGS:
"You do not need to unlock bootloader or to root the phone if you want to flash a stock firmware from XperiFirm.
There are no files in the stock firmware that need to be deleted. Prompts will ask you to skip some files.
Feel free to press N to every prompt since:
- TA dumping it's not related with DRM keys.
- Flash persist_* files only if you know what you are doing, since you will lose your attest keys. Backup persist partition.
If you need the firmware on both A and B slot use fastboot commands to choose the inactive partion and re-flash."


## Flash twrp recovery

```
fastboot flash recovery twrp-3.3.1-0-lilac-android10-1.img
fastboot boot twrp-3.3.1-0-lilac-android10-1.img
```

## Flash lineageos wirth twrp

```
adb sideload lineage-18.1-20210120-UNOFFICIAL-v2.0-lilac.zip
```
