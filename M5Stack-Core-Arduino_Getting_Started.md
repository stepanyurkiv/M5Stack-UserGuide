# M5Stack-Core-Arduino —— Getting Started


---

## 一、安装USB驱动

点击以下链接，下载M5Stack-Core的USB转串口驱动

https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers

下载完之后，解压，根据系统位数，双击对应可执行文件

(Windows 32位，执行CP210xVCPInstaller_x68.exe；Windows 64位，执行CP210xVCPInstaller_x64.exe；)

*判断驱动安装是否成功：*
如果安装成功，在插入M5Stack主控之后，设备管理器如下图所示出现，Silicon Labs的CP21x系列串口端口号
(我的电脑当前串口号是COM3)

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/my_com.png)


## 二、开发环境
## **Windows**
### 1、安装Arduino IDE

*下载地址*
https://www.arduino.cc/en/Main/Software 

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/arduino_cc_package.png)


如下图所示修改Arduino路径为D:\Program Files

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/select_arduino_install_path.png)


此时，Arduino的安装路径为D:\Program Files\Arduino

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/arduino_path.png)



### 2、Arduino IDE中下载M5Stack的库

打开Arduino IDE之后，选择“项目”->“加载库”->“管理库...”，搜索“M5Stack”并点击“安装”

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/select_arduino_lib.png)

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/download_m5stack_lib.png)



### 3、下载ESP32相关支持包

（我的Arduino当前路径是D:\Program Files\arduino-1.8.5）

进入Arduino安装路径的hareware文件夹，按住Shift键的同时，右键选择“在此处打开命令窗口”


在打开的Windows终端CMD中输入如下命令

> * 创建espressif目录，并切换到此目录下

mkdir espressif && cd espressif

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/mkdir_espressif.png)


> * 将esp32的支持包clone在文件夹esp32下

git clone https://github.com/espressif/arduino-esp32.git  esp32

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/clone_esp32_idf.png)


> * 切换到esp32路径，进一步clone子仓库文件

cd esp32

git submodule update --init --recursive

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/clone_esp32_idf_subdir.png)



### 4、下载ESP32编译链tools

进入此路径[YOUR_ARDUINO__DIR]/hardware/espressif/esp32/tools
选中并双击执行get.exe文件

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/select_get_exe_file.png)

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/download_xtensa_tools.png)


## 三、示例

USB线连接M5Stack主控，选择串口和一个示例程序，compile and upload

### 1、打开一个示例程序，如打开FactoryTest.ino

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/select_demo.png)



确认连接板子名称、串口波特率和当前串口号分别：M5Stack-Core-ESP32、921600、COM3(当前电脑串口号)

![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/select_board_and_com.png)


编译运行成功之后，串口监视窗口显示如下


![image](https://github.com/watson8544/M5Stack-UserGuide/blob/master/screenshots/FactoryTest_result.png)

### 2、新建一个M5Stack程序

打开Arduino IDE之后，新建.ino文件，并保存为my_test.ino。

将如下代码拷贝进文件中。

```cpp
#include <M5Stack.h>

// the setup routine runs once when M5Stack starts up
void setup(){tack

  // Initialize the M5Stack object
  M5.begin();

  // LCD display
  M5.Lcd.print("Hello World!");
  M5.Lcd.print("M5Stack is running successfully!");    
}

// the loop routine runs over and over again forever
void loop() {

}
```

点击编译运行，此时M5Stack显示器显示"Hello World!""M5Stack is running successfully!"


                                                                            *Last updated on 2018-06-08*


                                                                            