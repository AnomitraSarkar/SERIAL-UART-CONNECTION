# SYSTEM WORKING

if using ttyS0 when using UART communication
if using ttyACM0 when using Serial communication

<Connection: Rx Tx to Tx Rx and common GROUND>

### General Setup for Raspberry PI

reference youtube link: [Configure Serial Raspberry Pi 4B-UART-GPIO 14 and 15] (https://www.youtube.com/watch?v=oevxqPk78sM)

<INSTRUCTION: No need for the following the last step but concur the working of UART and ttyS0, check with USB serial then UART>

### This is setup in raspberry for Serial/UART

```python

import serial

ser = serial.Serial("/dev/ttyACM0")
ser.setDTR(False) #to make the flush input work
ser.flushInput()
ser.setDTR(True)
# give delay between them

```

### methods to read and write for Serial/UART

```python
ser.write(b'1') #byte conversion "b" write in front

ser.read() #---> "b" in byte conversion check
```

### Setup for arduino

```c++
void setup() {
    Serial.begin(9600);
    while (!Serial){
        // wait for serial port to connect, needed for native usb serial connection
    }
}
// set baud rate
```

### methods to read and write for Serial/UART

```c++
void loop()
{
    if (Serial.available() > 0) // always initialize availablity
    {
        Serial.read() // character reading use data type accordingly
        Serial.write("A", 1) // buffer stream character and length in character
    }
}
```
