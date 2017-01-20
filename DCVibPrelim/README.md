#Preliminary DC Controller

This is a preliminary test that uses an Arduino microcontroller to adjust the speed of a DC cell phone vibrator motor.
For pictures and a video demo, follow the Box Link: https://ucmerced.box.com/s/9qjkkzlt37kru2nd51f918z302qu677p

The actual project may or may not utilize a DC motor vibrator

Transistors are electronic switches. For schematics, NPN are “not pointing in” and amplify a current at the base. Using an NPN (PN2222) or PNP (BC558) will determine if high or low signals from the base will cause electricity to flow. 
(for an NPN, a high base will allow electricity to flow, and for a PNP a low base will allow electricity to flow.

The diode across the DC motor terminals will prevent negative voltage spikes from damaging the Arduino when the motor is turned off.

The code is developed to accept a serial value between 0 and 255 to alter the PWM of pin 3.

![pwm-arduino](https://cloud.githubusercontent.com/assets/14209170/22125759/d062283a-de49-11e6-9edd-73b917d298e8.gif)

For a 16 MHz Arduino the ADC clock is set to 16 MHz/128 = 125 KHz. Each conversion in AVR takes 13 ADC clocks so 125 KHz /13 = 9615 Hz
The actual sampling rate may vary, but this could play a role when determining what we actually want to use as the vibration source & controller.

Using PWM is not the cleanest way to control the motor. It would probably be better to use a simple potentiometer to adjust the speed, but an Arduino could be programmed as a tachometer that reads the actual speed in RPM. 
To convert from RPM to Hz, we just divide by 60 since there are 60 seconds per minute and Hertz are a number of vibrations per second. The tachometer can just be an IR break beam/ reflection, or hall encoder.

![wiring schematic](https://cloud.githubusercontent.com/assets/14209170/22127502/f49b8f78-de50-11e6-8a8c-468e15c0a20b.jpg)

Some next steps:
- Design a mounting unit with a tachometer (IR or Hall sensor)
- Display actual RPM read by tacho
- Adjust RPM via potentiometer
- Create a "Sweeping" function that increases and dereases the frequency
- Connect the device via bluetooth
- Control and display on a phone app
