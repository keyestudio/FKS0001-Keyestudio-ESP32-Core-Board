### Project 1 LED Blinking

**1.Description**

LED blinking is a simple project designed for starters. You only need to install an LED on Arduino board and upload the code on Arduino IDE. This project reinforces the lear ning of Arduino conceptual framework and using methods for starters. 

**2. Working Principle**

![](./media/A16.png)

- **LED:** The above is the circuit diagram of LED. Generally speaking, limited IO ports of output current may cause low brightness of LED, so a NPN triode (Q2) is applied in circuit as a switch. In this case, the LED will light up if the base(pin 1) of triode is at a high level. On the contrary, LED goes off when the base is at low. 

- **Triode switch:** To have a clear idea of its principle, certain knowledge of electronic circuit is required. For details, please consult materials by yourself. Briefly, LED on and off rely on the high and low levels of triode base, which are decided by the pin on the development board. LED lights up when the base(pin 1) is at a high level, and it goes off when the base is at low.

**3.Wiring Diagram：**

![](./media/A17.png)

**4.Upload Code**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 1: LED Blinking
  http://www.keyestudio.com
*/
int ledPin = 5; //Define LED to connect with pin IO5
void setup() 
{
  pinMode(ledPin, OUTPUT);//Set the mode to output
}

void loop() 
{
  digitalWrite(ledPin, HIGH); //Output a high level, LED lights up
  delay(1000);//Delay 1000ms 
  digitalWrite(ledPin, LOW); //Output a low level, LED goes off
  delay(1000);
}
```

**5.Test Result**

After uploading the code and powering on, LED will light up for 1s and off for 1 s.

