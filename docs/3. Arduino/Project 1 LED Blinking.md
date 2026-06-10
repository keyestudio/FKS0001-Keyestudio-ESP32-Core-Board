### Projekt 1 LED Blinken

**1. Beschreibung**

LED Blinken ist ein einfaches Projekt, das für Einsteiger konzipiert wurde. Sie müssen nur eine LED auf dem Arduino-Board installieren und den Code in der Arduino IDE hochladen. Dieses Projekt festigt das Verständnis des Arduino-Konzeptframeworks und die Anwendungsmethoden für Anfänger.

**2. Funktionsprinzip**

![](media/A16.png)

- **LED:** Oben ist das Schaltbild der LED dargestellt. Allgemein gesprochen kann die begrenzte Ausgangsstromstärke der IO-Ports zu einer niedrigen Helligkeit der LED führen, daher wird im Schaltkreis ein NPN-Transistor (Q2) als Schalter verwendet. In diesem Fall leuchtet die LED, wenn die Basis (Pin 1) des Transistors auf hohem Pegel ist. Im Gegensatz dazu geht die LED aus, wenn die Basis auf niedrigem Pegel ist.

- **Transistorschalter:** Um das Prinzip klar zu verstehen, sind gewisse Kenntnisse der Elektronik erforderlich. Für Details konsultieren Sie bitte entsprechende Materialien. Kurz gesagt, das Ein- und Ausschalten der LED hängt von den hohen und niedrigen Pegeln der Transistorbasis ab, die durch den Pin auf dem Entwicklungsboard bestimmt werden. Die LED leuchtet, wenn die Basis (Pin 1) auf hohem Pegel ist, und geht aus, wenn die Basis auf niedrigem Pegel ist.

**3. Schaltplan：**

![](media/A17.png)

**4. Code hochladen**

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

**5. Testergebnis**

Nach dem Hochladen des Codes und Einschalten der Stromversorgung leuchtet die LED für 1 Sekunde und ist dann für 1 Sekunde aus.