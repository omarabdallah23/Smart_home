# Smart home project
## List of contents:
1. Introduction.
2. Front yard lighting.
3. AC control system.
4. Gate control system.
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

This system consists of the following:
1. Slave microcontroller.
2. Button.
3.  L298 motor driver.
4.  DC motor.

By pressing the button, you change the current state of the gate. If the gate was initially open it closes and vice versca. The last state of the gate is saved in the internal EEPROM of the slave microcontroller.
The motor changes its direction of motion whether clockwise or counter-clockwise each time the button is pressed.

## Notes and warnings:
> [!NOTE]
> This code was written with a software layer-based approach, meaning that the code consists of 3 layers :
> 1. MCAL layer which contains the modules for the microcontroller's internal peripherals.
> 2. ECU layer which contains the modules for a number of external devices that can be connected to the microcontroller.
> 3. Application layer which contains the actual code of the project itself

> This approach provides isolation between each layer and the layers below it, meaning that you can change the application layer code without modifying the MCAL or ECU layers.

> [!NOTE]
> The drivers used, whether in MCAL or ECU layer, were programmed from scartch for my own educational purposes however, you don't have to program the drivers yourself as
> MPLAB X IDE provides built-in drivers which will save you a lot of time.

> [!IMPORTANT]
> The front yard lighting sytem needs to be placed in a shade-free environmet to avoid wrong operation of the system.

> [!CAUTION]
> Connecting the PWM to the slave microcontroller will increase the CPU load significantly which in turn decrease the speed of the simulation. If you wish to test components other than the PWM, i suggest
> disconnecting the PWM pin first. 
