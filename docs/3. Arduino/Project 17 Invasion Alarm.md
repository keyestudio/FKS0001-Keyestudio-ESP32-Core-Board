### Projekt 17 Einbruchalarm

**1. Beschreibung**

Dieses Einbruchalarmsystem kann Eindringlinge in Häusern oder kleinen Büros erkennen und den Besitzer rechtzeitig warnen, Maßnahmen zu ergreifen.

In diesem Projekt überwacht der Sensor einen bestimmten Bereich. Ein Gerät auf dem Arduino-Board löst aus, dass eine LED aufleuchtet und ein Summer ertönt, wenn in dieser Zone eine Bewegung erkannt wird.

Praktisch zeichnet sich dieses Modul durch einfache Installation und geringe Kosten aus. Neben dem Einsatz in Wohn- und Büroräumen eignet es sich auch für Fabriken, Lagerhäuser und Märkte, was in großem Maße den Schutz von Eigentum gewährleistet.

**2. Funktionsprinzip**

![](media/A64.png)

Der menschliche Körper (37°C) strahlt stets Infrarotstrahlung mit einer Wellenlänge von 10μm aus, die der vom Sensor erfassten Wellenlänge entspricht.

Daher ist dieses Modul in der Lage, Bewegungen von Menschen zu erkennen. Wenn eine Bewegung erkannt wird, gibt der PIR-Sensor für etwa 3 Sekunden ein High-Signal aus. Andernfalls gibt er ein Low-Signal aus.

**3. Schaltplan**

![](media/A65.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.1 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;    //Define IO5 as PIR sensor pin 

void setup() 
{
  pinMode(pir,INPUT);   //Set IO5 pin to input 
  Serial.begin(9600);
}

void loop() 
{
  int pir_val = digitalRead(pir); 	//Read the PIR result and assign it to pir_val 
    Serial.print("pir_val:"); //Print “pir_val”
	Serial.println(pir_val);
    delay(500);
}
```

**5. Testergebnis**

Nach dem Verbinden der Schaltung und Hochladen des Codes öffnen Sie den seriellen Monitor, stellen die Baudrate auf 9600 ein, und der serielle Port gibt den PIR-Wert aus. Wenn der PIR-Sensor eine Person erkennt, wird eine 1 angezeigt.

![](media/A66.png)

**6. Wissens** Erweiterung

Lassen Sie uns einen Einbruchalarm bauen. Wenn der PIR-Sensor einen Menschen erkennt, leuchtet die LED auf und der Summer gibt einen Ton von sich. Andernfalls erlischt die LED und der Summer bleibt stumm.

- **Flussdiagramm：**

![](media/A67.png)

- **Schaltplan：**

![](media/A68.png)

- **Code：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.2 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;		//Set PIR sensor pin to IO5
int red_led = 18;	//Set red LED to pin IO18
int buzz = 19;		//Set buzzer to pin IO19

void setup() 
{
  // put your setup code here, to run once:
  pinMode(pir,INPUT);		//Set PIR pin to input mode 
  pinMode(red_led,OUTPUT);	//Set LED pin to output mode  
  pinMode(buzz,OUTPUT);		//Set buzzer pin to output mode 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int pir_val = digitalRead(pir);
  if(pir_val == 1)
  {
    digitalWrite(red_led,HIGH);
    digitalWrite(buzz,HIGH);
  }
  else
  {
    digitalWrite(red_led,LOW);
    digitalWrite(buzz,LOW);
  }
}
```

**Testergebnis**

Wenn der PIR-Sensor eine Person in der Nähe erkennt, leuchtet die rote LED auf und der Summer ertönt.