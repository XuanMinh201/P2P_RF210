# P2P for RF210 - SCAPA
This git for examples P2P using module RAK3172 and MCU ESP32-C3
# Overview

![image](https://github.com/XuanMinh201/P2P---RF210/assets/75436464/b5e0e804-5fc7-4523-b13d-a74fae75ba62)

RF210 board includes:
-  Use RAK3172 module to implement LoRa P2P
-  Use MCU ESP32-C3 to control RAK3172 via [AT-Command](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#overview)  and a few [ATC-Command](https://github.com/XuanMinh201/P2P---RF210/edit/main/README.md) commands
-  Collect I2C sensor data
-  Sw2 is a power switch with 3 levels. Turn on the left to use USB power (5V), turn on the right to use Battery power, in the middle is to turn off the power
-  Sw1 is the UART switch, it connects Uart0 of the ESP32-C3 with Uart 2 of the RAK3172. To use AT command, Sw1 must be turned on

# P2P có 2 cách
## tự P2P bằng rak
## P2P sử dụng ESP32

## Softwave


### Aruino
### STM32

## Hardwave

# ATC comnmand 


