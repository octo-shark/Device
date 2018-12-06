# Device - Time Shark - Time Pylon

Uses Arduino Uno,
MPU6050 accelerometer &
HC-5U Bluetooth modem

This code reads the MPU6050 and sends the x,y,z vector and which side is facing up to the
bluetooth modem and the serial port.

Bluetooth modem runs at 9600 baud<br>
Built-in serial port is at 57600 baud

Built-in arduino serial port outputs in following format:

```
{"side":[0..7], "ax":[-2..2], "ay":[-2..2], "az":[-2..2]}

example:
{"side":0, "ax":.03, "ay":1.24, "az":-1.02}
```

Bluetooth serial output:<br>
Bluetooth modem sends side in JSON format when a new side is set.

```
{"side":[0..7]}

example:
{"side":0}
```

To start time pylon:

First, Link Time Pylon with Mac over Bluetooth

1. Goto System prefs -> Bluetooth
2. Turn on device (bluetooth LED rapid flashing)
3. Wait 10s for HC-05 to appear
4. Click "Pair" with HC-05, _first attempt will fail_
5. Click "Options..."
6. Enter 1234 for access code & click connect
7. Bluetooth is now ready

to start Time Pylon Device server:<br>
npm run go

To view sample web app:<br>
http://localhost:8080/echotest.html

Wiring:
Arduino pin 9 RX -> HC-05 TXD<br>
Arudino pin 10 TX -> HC-05 RXD<br>
Arduino pin A4 -> MPU6050 SDA<br>
Arduino pin A5 -> MPU6050 SCL<br>
Arduino 3.3v -> MPU6050 VCC<br>
Arduino 5v -> HC-05 Vcc<br>
Ardunio gnd -> MPU6050 GND<br>
Arduino gnd -> HC-05 GND<br>
Arduino pin 2 -> MPU6050 INT<br>

`````
             /""-._
            .      '-,
            :         '',
            ;      *     '.
            ' *         () '.
             \               \
              \      _.---.._ '.
               :  .' _.--''-''  \ ,'
                '/.'             . ;
                 ,                \'
                  \               /          ___.--,
           _.._     \           /     _.---'`__.-( (_.
     __.--'`_.. '.__.\    '--. \_.-' ,.--'`     `""`
   ( ,.--'`   ',__ /./;   ;, '.__.'`    __
   _`) )  .---.__.' / |   |\   \__..--""  """--.,_
   `---' .'.''-._.-'`_./  /\ '.  \ _.-~~~````~~~-._`-.__.'
         | |  .' _.-' |  |  \  \  '.               `~---`
         \ \/ .'     \  \   '. '-._)
           \/ /        \  \    `=.__`~-.
          / /\         `) )    / / `"".`\
    , _.-'.'\ \        / /    ( (     / /
     `--~`   ) )    .-'.'      '.'.  | (
             (/`    ( (`          ) )  '-;
             `      '-;         (-'
`````
