# P2P for RF210 - SCAPA
This git for examples P2P using module RAK3172 and MCU ESP32-C3
# Overview

![image](https://github.com/XuanMinh201/P2P---RF210/assets/75436464/b5e0e804-5fc7-4523-b13d-a74fae75ba62)

RF210 board includes:
-  Use RAK3172 module to implement LoRa P2P
-  Use MCU ESP32-C3 to control RAK3172 via [AT-Command](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#overview)  and a few ATC-Command
-  Collect I2C sensor data
-  Sw2 is a power switch with 3 levels. Turn on the left to use USB power (5V), turn on the right to use Battery power, in the middle is to turn off the power
-  Sw1 is the UART switch, it connects Uart0 of the ESP32-C3 with Uart 2 of the RAK3172. To use AT command, Sw1 must be turned on

# P2P for RAK3172

To use this function, you need to upload the Bridge code and use serial to enter AT-commnad commands

- To use P2P requires at least 2 devices. One to receive, one to send
- Some notes before using P2P with AT-Command:
  - You need to direct the device to P2P mode using the command [AT+NWM=0](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#at-nwm)
    
![image](https://github.com/XuanMinh201/P2P---RF210/assets/75436464/4dd216ee-28b8-4089-a9a5-d40c47cfbacf)
 
  - Config parameters for P2P [AT+P2P=869525000:7:250:0:8:15](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#at-p2p)
  
![image](https://github.com/XuanMinh201/P2P---RF210/assets/75436464/7de60288-af39-40ce-bd99-c204c53b5a35)

  - Config for the receiving device [AT+PRECV=65534](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#at-precv). There are many configurations, so read this command carefully before using it depending on your needs
  - Config for the sending device [AT+PSEND=11223344](https://docs.rakwireless.com/RUI3/Serial-Operating-Modes/AT-Command-Manual/#at-psend).

![image](https://github.com/XuanMinh201/P2P---RF210/assets/75436464/98565e5a-97cd-4844-a9f1-e1cabe244567)

## Softwave


### Aruino
### STM32

## Hardwave

# ATC comnmand 

Command general format: ```ATC+<cmd>=?```

- ```ATC+VER=?``` : return version of the firmware

- ```ATC+SHT=?``` : return 1 if sensor is available, return 0 of not
- ```ATC+TEMP=?``` : return the value of temperature with 0.01° resolution, return 0 if not available
- ```ATC+HUM=?``` : return the value of humidity with 1% resolution, return 0 if not available

- ```ATC+KX023=?``` : return 1 if sensor is available, return 0 of not
- ```ATC+AX=?``` : return the value of X acceleration with 0.01G resolution, return 0 if not available
- ```ATC+AY=?``` : return the value of Y acceleration with 0.01G resolution, return 0 if not available
- ```ATC+AZ=?``` : return the value of Z acceleration with 0.01G resolution, return 0 if not available

- ```ATC+LTR=?``` : return 1 if sensor is available, return 0 of not
- ```ATC+LUMCH0=?``` : return the value of CH0, return 0 if not available
- ```ATC+LUMCH1=?``` : return the value of CH1, return 0 if not available
- ```ATC+LUM=?``` : return the value of CH1, return 0 if not available

- ```ATC+GPS=?``` : return 1 if sensor is available, return 0 of not
- ```ATC+GPSFIX=?``` : return 1 if GNSS get a fix, return 0 of not
- ```ATC+GPSON=<1/0>``` : Turn ON/OFF GPS LDO, return HIGH/LOW 
- ```ATC+GPSSAT=?``` : return number of satellite available
- ```ATC+GPSTIME=?``` : return GPS time in EPOCH format, 0 if not available
- ```ATC+GPSLAT=?``` : return GPS Latitude, 0 if not available
- ```ATC+GPSLON=?``` : return GPS Longitude, 0 if not available
- ```ATC+GPSALT=?``` : return GPS Altitude, 0 if not available
- ```ATC+GPSNMEA=<1/0>``` : Activate NMEA log from GNSS module
- ```ATC+GPSLOG=<1/0>``` : Activate GNSS Log from GNSS module
- ```ATC+GPSDC=<1/0>``` : Set GNSS module in duty cycle mode with 30sec sleep

- ```ATC+BAT=?``` : return battery voltage in mv, 0 if not available
- ```ATC+LDO=?``` : return LDO voltage on Rak3172 in mv, 0 if not available

See details at [RF210](https://github.com/XuanMinh201/RF210)
