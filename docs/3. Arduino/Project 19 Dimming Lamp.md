### Projekt 19 Dimmbares Licht

**1. Beschreibung**

Die dimmbare Lampe passt die Helligkeit der LED über ein Potentiometer und einen Arduino-Controller an. Die Helligkeit hängt vom Widerstandswert ab, der durch Anschluss der Enden des Potentiometers an digitale oder analoge Pins auf dem Board ausgelesen und eingestellt werden kann. Darüber hinaus wird dieses System zur Steuerung der Spannung oder des Stroms anderer Geräte wie Lüfter, Glühbirnen und Heizungen verwendet.

**2. Funktionsprinzip**

![](media/B3.png)

![](media/B4.png)

Im Wesentlichen ist ein Potentiometer ein Bauelement, das den Widerstandswert verändern kann. Nach dem Ohmschen Gesetz (U=I*R) beeinflusst der Widerstand die Spannung. Unser Potentiometer hat 10K.

In diesem Projekt beträgt der maximale Widerstand 10K. Das ESP32-Board teilt die Spannung von 3V gleichmäßig in 4095 Teile (3/4095=0.0007326007326). Die analoge Spannung wird durch Multiplikation des ausgelesenen Werts mit 0.0007326007326 erhalten.

**3. Schaltplan**

![](media/B5.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.1 Dimming Lamp
  http://www.keyestudio.com
*/
int pot = 34;      //Define variable pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);	//Read io34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes öffnen Sie den seriellen Monitor, stellen die Baudrate auf 9600 ein, und der analoge Wert wird im Bereich von 0-4095 angezeigt. Das Drehen des Potentiometers ändert die Größe des analogen Werts.

![](media/B6.png)

**6. Wissensvertiefung**

Wir steuern die Helligkeit der LED über ein Potentiometer. Wie bekannt, wird dies durch PWM beeinflusst. Der Bereich des analogen Werts liegt jedoch bei 0-4095, während der von PWM bei 0-255 liegt. Daher wird eine Funktion „map(value, fromLow, fromHigh, toLow, toHigh)“ benötigt.

**Schaltplan：**

![](media/B7.png)

**Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.2 Dimming Lamp
  http://www.keyestudio.com
*/
int led = 25;		//Define LED to IO25
int pot = 34;		//Define pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  pinMode(led,OUTPUT);		//Set LED pin to output 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);
  int led_val = map(value,0,4095,0,255);  //Convert the range of potentiometer analog value to the range we need  
  analogWrite(led,led_val);
}
```

**7. Testergebnis**

Nach erfolgreichem Hochladen des Codes ändert das Drehen des Potentiometers die Helligkeit der roten LED.