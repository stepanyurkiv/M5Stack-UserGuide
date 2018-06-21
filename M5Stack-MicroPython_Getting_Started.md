# M5Stack-Core-MicroPython —— Getting Started

## content
- [Download M5Cloud Firmware](#Download-M5Cloud-Firmware)
- [Download](#Download)

### Download M5Cloud Firmware

https://github.com/m5stack/M5Cloud/tree/master/firmwares

Now, the M5Cloud firmware I downloaded named `m5cloud-20180516-v0.4.0.bin`

***Windows***



***MacOS/Linux***
**1. Check port on Linux and MacOS**

  To check the device name for the serial port of your M5Stack board (or external converter dongle), run this command two times, first with the board / dongle unplugged, then with plugged in. The port which appears the second time is the one you need:

  Linux

  ```
  ls /dev/tty*
  ```
  
  MacOS

  ```
  ls /dev/cu.*
  ```


**2. Adding user to `dialout` on Linux**

The currently logged user should have read and write access the serial port over USB. On most Linux distributions, this is done by adding the user to `dialout` group with the following command:

  ```
  sudo usermod -a -G dialout $USER
  ```
Now, my serial port named `ttyUSB0`

[^_^]:
    TODO: put a picture here


**2. Download M5Cloud firmware to M5Stack board**

* Installing esptool：
```
pip install esptool
```

* Erase flash on M5Stack:

```
esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash
```

* Download firmware to M5Stack: 

```
esptool.py --chip esp32 --port /dev/ttyUSB0 write_flash --flash_mode dio -z 0x1000 m5cloud-20180516-v0.4.0.bin
```

### Download