
### CONTENT

[Download M5Cloud Firmware to M5Stack board](#download-m5cloud-firmware-to-m5stack-board)

[1. Download M5Cloud Firmware from Github](#1-download-m5cloud-firmware-from-github)
   
[2. M5Cloud Firmware to M5Stack board](#2-m5cloud-firmware-to-m5stack-board)

[M5Stack board connect io.m5stack.com via Wi-Fi](#m5stack-board-connect-iom5stackcom-via-wi-fi)

[Binding device](#binding-device)

[Coding MicroPython](#coding-micropython)


### Download M5Cloud Firmware to M5Stack board
####1. Download M5Cloud Firmware from Github
https://github.com/m5stack/M5Cloud/tree/master/firmwares

Now, the M5Cloud firmware I downloaded named `m5cloud-20180516-v0.4.0.bin`
And `m5cloud-20180516-v0.4.0.bin` saved at `~/smbshare`, as shown below

####2. M5Cloud Firmware to M5Stack board
![image](platform_picture/windows-logo1.png) | ![image](platform_picture/linux-logo1.png) | ![image](platform_picture/macos-logo1.png) 
---|---|---
Windows | Linux | MacOS 

***Windows***



***MacOS/Linux***
*1. Check port on Linux and MacOS*

  To check the device name for the serial port of your M5Stack board (or external converter dongle), run this command two times, first with the board / dongle unplugged, then with plugged in. The port which appears the second time is the one you need:

  Linux

  ```
  ls /dev/tty*
  ```
  
  MacOS

  ```
  ls /dev/cu.*
  ```


*2. Adding user to `dialout` on Linux*

The currently logged user should have read and write access the serial port over USB. On most Linux distributions, this is done by adding the user to `dialout` group with the following command:

  ```
  sudo usermod -a -G dialout $USER
  ```
Now, my serial port named `ttyUSB0`

*3. Download M5Cloud firmware to M5Stack board*

  - Installing esptool：
    ```
    pip install esptool
    ```

  - Erase flash on M5Stack:
    ```
    esptool.py --chip esp32 --port /dev/ttyUSB0 erase_flash
    ```

  - Download firmware to M5Stack: 
    ```
    esptool.py --chip esp32 --port /dev/ttyUSB0 write_flash --flash_mode dio -z 0x1000 m5cloud-20180516-v0.4.0.bin
    ```
    
###3. M5Stack board connect io.m5stack.com via Wi-Fi


Mobile Phone or PC connect to M5Stack AP(like `M5Stack-a67c`), and then open brower to login 192.168.4.1 setting your LAN SSID and Password

![image](M5Stack_MicroPython_UserGuidePictures/m5stack_connet_wifi.png)

###4. Binding device

*1.login io.m5stack.com and register your own account(or login your account)*

*2. press `Device->Add` buttom on M5Cloud IDE for binding M5Stack board to your account*

*3. Input the Check Code for the M5Stack screen display，Check Code is random,after 60s will refresh*

![image](M5Stack_MicroPython_UserGuidePictures/check_code_on_m5stack.png)

![image](M5Stack_MicroPython_UserGuidePictures/WebIDE_check_code.png)

###5. Coding MicroPython

*1. create a new python project*

![image](M5Stack_MicroPython_UserGuidePictures/create_a_new_project.png)

*2. press `Upload & Run` buttom on the M5Cloud IDE*

![image](M5Stack_MicroPython_UserGuidePictures/hello_world_prj.png)
