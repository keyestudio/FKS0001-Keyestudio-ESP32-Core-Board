### Project 25 Ultrasonic Rangefinder

**1. Description**

This ultrasonic rangefinder measures distance of obstacles by emitting sound waves and then receiving the echo. That is to say, the distance is not an immediate value, but an observed one by a theoretical calculation of time difference between emitter and receiver. 

Ultrasonic is able to detect the shape of objects, set up automatic doors and estimate flow velocity and pressure. 

What's more, it supports cooperative works with computers. As a result, the measured value can be transmitted to computers via Arduino board. 

In daily life, it is widely used for motors, servos and LEDs as well as systems(automatic navigation, control and security monitoring systems).

**2. Working Principle**

![](media/B91.png)

As we all know, ultrasonic is a kind of inaudible sound wave signal with high frequency. Similar to a bat, this module measures distance of obstacles by calculating the time difference between wave-emitting and echo-receiving.

- **Maximum distance:** 3M

- **Minimum distance:** 5cm

- **Detection angle:** ≤15°

**3. Wiring Diagram**

![](media/B92.png)

**4. Test Code**

In "forever" block, construct two "serial print" blocks and drag a "read distance" block from “Ultrasonic”. Set trig pin to IO13 and echo pin to IO14 both in cm. Do not forget a delay of 0.5s. 

![](media/B93.png)

**5. Test Result**

After connecting the wiring and uploading code, open serial monitor to set baud rate to 9600, and the serial port starts to print the distance value. 

![](media/B94.png)

**6. Knowledge Expansion**

Let's make a rangefinder. 

We display characters on LCD 1602. Program to show "Keyestudio" at (3,0) and “distance:” at (0,1) followed by the distance value at (9,1). 

When the value is smaller than 100(or 10), a residue of the third(or the second) bit still exists. Therefore, an "if" judgement is necessary to determine a certain condition.

**Wiring Diagram：**

![](media/B95.png)

**Code：**

1. Drag the two basic blocks.

2. In "LCD", initialize the LCD. Drag an “LCD print” block and add character string “Keyestudio” (It also can be put out of "forever" block as this display is fixed). Add a "variable" block and set type to int and name to "distance" with an initial assignment of 0.

![](media/B96.png)

3. Assign the read distance value to the variable "distance". Set the LCD to print “Distance：” and followed by the distance value (and we need calculate the front displayed characters in advance to set a cursor followed them).

![](media/B97.png)

4. Build a "clear display residue" block when the number of displayed bits decrease. We firstly adopts a condition to judge whether the distance is smaller than 100(or 10). If so, a space will be printed at the residue of the third (or the second) bit to clear previous display. Lastly, don't forget to add a delay of 0.5s. 

![](media/B98.png)

**Complete Code:**

![](media/B99.png)

**7. Code Explanation**

Read the distance after setting the trig pin and echo pin. The unit of displayed value is optional (cm or inch).

![](media/B100.png)

