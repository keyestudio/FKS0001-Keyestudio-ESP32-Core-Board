### Projekt 4 Ampel

**1. Beschreibung**

Das Ampelmodul ist ein Gerät zur Steuerung des Verkehrs von Fußgängern und Fahrzeugen. Es umfasst eine rote, eine gelbe und eine grüne Lampe, die unterschiedliche Anweisungen bedeuten.

**Rot für Stopp:** Fußgänger und Fahrzeuge halten an.

**Gelb für Vorsicht:** Fußgänger und Fahrzeuge bereiten sich auf das Anhalten vor. Wenn die Fahrt bereits im Gange ist, sollte die Geschwindigkeit reduziert werden.

**Grün für Weiterfahren:** Fußgänger und Fahrzeuge fahren unter Beachtung der Verkehrsregeln weiter.

In diesem Projekt können Sie Arduino verwenden, um Code zur Steuerung der Ampel zu schreiben. Zum Beispiel können Sie die Dauer jeder Lampe und die Zeitintervalle dazwischen einstellen. Außerdem können Sie einen Timer hinzufügen, um die Lichtfarben nach einem Zeitplan zu ändern.

**2. Schaltplan**

![](media/A21.png)

**3. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 4 Traffic Light
  http://www.keyestudio.com
*/
int greenPin = 27;   //Green LED connects to IO27
int yellowPin = 26; //Yellow LED connects to IO26
int redPin = 25;   //Red LED connects to IO25

void setup() 
{
  //Set all LED interfaces to output mode
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(redPin, OUTPUT);
}

void loop() 
{
  digitalWrite(greenPin, HIGH); //Light green LED up 
  delay(5000);  //Delay 5s
  digitalWrite(greenPin, LOW); //Turn green LED off 
  for (int i = 1; i <= 3; i++) //Execute for 3 times
  {  
    digitalWrite(yellowPin, HIGH); //Light yellow LED up
    delay(500); //Delay 0.5s
    digitalWrite(yellowPin, LOW); // Turn yellow LED off
    delay(500); //Delay 0.5s
  }
  digitalWrite(redPin, HIGH); //Light red LED up 
  delay(5000);  //Delay 5s 
  digitalWrite(redPin, LOW); //Turn red LED off 

}
```

**4. Testergebnis**

Nach dem Hochladen des Codes leuchtet die grüne LED für 5 Sekunden, die gelbe LED blinkt 3-mal und die rote LED leuchtet für 5 Sekunden, und das in einem Zyklus.