### Projekt 7 Aktiver Summer

**1. Beschreibung**

Ein aktiver Summer ist eine Komponente, die als Alarm, Erinnerung oder Unterhaltungsgerät verwendet wird und einen zuverlässigen Klang bietet. Darüber hinaus ermöglicht er die Erzeugung hochgradig kontrollierbarer Töne, wodurch unsere Projekte interessanter werden.

**2. Funktionsprinzip**

![](media/A26.png)

Ein aktiver Summer integriert einen Multivibrator, daher erzeugt er nur durch Gleichspannung Ton. Pin 1 des Summers wird mit VCC verbunden und Pin 2 wird durch einen Transistor gesteuert. Wenn für die Basis (Pin 1) des Transistors ein hoher Pegel anliegt, verbinden sich dessen Kollektor (Pin 3) und Emitter (Pin 2) mit GND, und der Summer gibt einen Ton von sich.

Umgekehrt, wenn wir der Basis einen niedrigen Pegel geben, werden die übrigen Pins getrennt, sodass der Summer still bleibt.

**3. Schaltplan**

![](media/A27.png)

**4. Testcode**

```
 /*
  keyestudio ESP32 Inventor Learning Kit
  Project 7 Active Buzzer
  http://www.keyestudio.com
*/
int buzzer = 5; //Define buzzer connected to IO5 pin 

void setup() 
{
  pinMode(buzzer, OUTPUT);//Set the output mode 
}

void loop() 
{
  digitalWrite(buzzer, HIGH); //IO5 pin outputs a high level to cause the buzzer to emit sound 
  delay(1000);					//Delay 1000ms
  digitalWrite(buzzer, LOW); //IO5 outputs a low level to prevent the buzzer to emit sound 
  delay(1000);
}
```

**5. Testergebnis**

Nach dem Hochladen des Codes und Einschalten gibt der Summer 1 Sekunde lang einen Ton von sich und bleibt anschließend 1 Sekunde still.