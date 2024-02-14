# Smart home project
## List of contents:
1. Introduction.
2. Front yard lighting.
3. AC control system.
4. Gate control system.
5. Conclusion.
## Introduction:
Smart home technology is a technology concerned with automating homes. For example instead of turning lights manually, lights can be programmed to turn on by itself  when it gets dark or instead of 
setting the temperature at which your AC or heater operate manually, they can be programmed to turn on or off depending on room temperature.
This smart home project will consist of the following:
1. Front yard lighting system.
2. AC control system.
3. Gate control system.
   
The schematic was designed on proteus 8 professional and the code was developed on MPLAB X IDE V6.15. The code was written in C and uploaded on PIC18f4620 microcontrollers

![smart home](https://github.com/omarabdallah23/smart_home/assets/143711494/0b5ac3b2-dbf6-4fdb-aebb-889df962bdb4)
## Front yard lighting system:
This system is designed to turn on and off the front yard light without doing it manually.

![Front yard lighting](https://github.com/omarabdallah23/smart_home/assets/143711494/43818734-5ebd-4557-b1bf-bd673a974600)

This system consists of the following components:
1. LDR sensor.
2. LED.
3. Master microcontroller.
   
Light dependent resistors or LDR for short are used to indicate the presence or the abscence of light, or to measure the light intensity. The microcontroller is programmed to send 5V to the LED as long as the LDR measures light intensity less than 300 lux. 300 lux was chosen because the light intensity of sunrise and sunset is between 300 and 500 lux. Once the LDR measures light intensity more than 300 lux, which indicates morning, the microcontroller will send 0V to LED which turns it off. 
## AC control system:
This system is designed to control the temperature of the room by controlling the air conditioning.

![AC control system](https://github.com/omarabdallah23/smart_home/assets/143711494/2e66e0bf-5fce-406d-924b-713a9ee22f6a)

This system consists of the following:
1. TC74 temperature sensor.
2. Master microcintroller.
3. Slave microcontroller.
4. LCD.
5. L298 motor driver.
6. DC motor.

The temperature sensor sends the current temperature value to master microcontroller. The master microcontroller performs 2 functions. Firstly it displays the temperature value on the LCD. Secondly it sends
characters to the slave microcontroller. 'b' indicates that the temperature is equal to 21 celsius and 'c' indicates that the temperature has exceeded 22 celsius. The slave microcintroller recieves these characters and acts accordingly. If the slave recieves 'b' it will turn on the motor with a 50% duty cycle. If the slave recieves 'c' it will turn on the motor with a 75% duty cycle. Otherwise the dc motor remains off. The TC74 temperature sensor, master microcontroller and slave microcontroller communicate with each other using I2C communication protocol. 
## Gate control system:
![Gate control system](https://github.com/omarabdallah23/smart_home/assets/143711494/021f6746-cc7c-4f72-a2f1-d158834dd342)
