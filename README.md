# Device - Time Pylon

Uses Arduino Uno,
MPU6050 accelerometer &
HC-5U Bluetooth modem

This code reads the MPU6050 and sends the x,y,z vector and which side is facing up to the 
bluetooth modem and the serial port.

Bluetooth modem runs at 9600 baud
Built-in serial port is at 57600 baud.

output:
Bluetooth modem sends side in JSON format when a new side is set:
{"side":[0..7]}

Bluetooth modem is hooked up to Arduino rx=pin 9, tx= pin 10

to start Device server:
npm run go

To view sample buil-in:
http://localhost:8080/echotest.html

Wiring:

Arduino pin 9  -> HC-05 TXD
Arudino pin 10 -> HC-05 RXD
Arduino pin A4 -> MPU6050 SDA
Arduino pin A5 -> MPU6050 SCL
Arduino 3.3v   -> MPU6050 VCC
Arduino 5v     -> HC-05 Vcc
Ardunio gnd    -> MPU6050 GND
Arduino gnd    -> HC-05 GND
Arduino pin 2  -> MPU6050 INT
