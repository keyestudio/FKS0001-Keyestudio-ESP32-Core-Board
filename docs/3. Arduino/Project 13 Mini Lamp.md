### **Projekt 13 Mini Lampe**

**1. Beschreibung**

In diesem Projekt steuern wir eine Lampe über Arduino UNO und einen Taster. Wenn wir den Taster drücken, ändert sich der Zustand der Lampe (AN oder AUS).

**2. Funktionsprinzip**

![](media/A53.png)

Wenn der Taster losgelassen wird, liefert eine Spannung VCC, die durch R29 fließt, ein High-Signal für den S-Anschluss. Beim Drücken werden Pin 1 und 3 sowie Pin 2 und 4 verbunden, und die Spannung an S1 wird auf GND gezogen, was ein Low-Signal darstellt. In diesem Moment verhindert R29 einen Kurzschluss zwischen VCC und GND.

**3. Schaltplan**

![](media/A54.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.1 Mini Lamp
  http://www.keyestudio.com
*/
int button = 15;
int value = 0;

void setup() 
{
  Serial.begin(9600); //Setze die serielle Baudrate auf 9600 
  pinMode(button, INPUT);  //Verbinde den Taster-Pin mit dem digitalen Port 8 und setze ihn auf Eingabemodus.
}

void loop() 
{
  value = digitalRead(button);//Lese den Wert des Tasters aus 
  Serial.print("Key status:"); //Gibt "Key status:" auf dem seriellen Port aus 
  Serial.println(value); //Gibt die Taster-Variable auf dem seriellen Port aus und fügt einen Zeilenumbruch hinzu
}
```

**5. Testergebnis**

Nach dem Verbinden der Schaltung und Hochladen des Codes öffne den seriellen Monitor und stelle die Baudrate auf 9600 ein.  
Wenn wir den Taster drücken, zeigt der serielle Port "Key status: 0" an; wenn wir ihn loslassen, zeigt der serielle Port "Key status: 1".

![](media/A55.png)

**6. Wissensvertiefung**

Als Nächstes steuern wir die LED über den Zustand des Tasters.

- **Flussdiagramm：**

![](media/A56.png)

- **Schaltplan:**

![](media/A57.png)

- **Code**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.2 Mini Lamp
  http://www.keyestudio.com
*/
#define led	   4
#define button 15
bool ledState = false;

void setup() 
{
  // initialisiere digitalen Pin PIN_LED als Ausgang.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT);
}

// die loop-Funktion läuft unendlich oft
void loop() 
{
  if (digitalRead(button) == LOW) {    //Wenn der Tasterwert zum ersten Mal 0 ist, wird Tasterprellen ausgelöst, daher wird 20 ms gewartet, um zu prüfen, ob der Taster weiterhin 0 ist. 
    delay(20);                              //20 ms Verzögerung
    if (digitalRead(button) == LOW) {   //prüfe, ob der Tasterwert 0 ist
      ledState = !ledState;                 //ledState wird auf den invertierten Wert gesetzt, um die LED ein- und auszuschalten 
      digitalWrite(led, ledState);
    }
    while (digitalRead(button) == LOW);     //halte die Schleife, solange der Taster gedrückt ist, verlasse sie beim Loslassen
  }
}
```

- **Testergebnis**

Du kannst die rote LED über den roten Taster ein- und ausschalten.