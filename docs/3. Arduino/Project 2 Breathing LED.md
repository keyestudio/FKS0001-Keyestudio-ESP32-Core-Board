### Projekt 2 Atmende LED

**1. Beschreibung**

Die Arduino atmende LED nutzt den programmierbaren PWM an Bord, um eine analoge Wellenform auszugeben. Nach dem Einschalten kann die Helligkeit der LED über den Tastgrad der Wellenform angepasst werden, um schließlich den Effekt einer atmenden LED zu realisieren.

Auf diese Weise kann Umgebungslicht simuliert werden, indem die LED-Helligkeit über die Zeit verändert wird. Außerdem kann die atmende LED ein farbenfrohes Mini-Licht bilden, um eine ruhige und warme Atmosphäre zu schaffen.

**2. Was ist PWM?**

PWM steuert analoge Ausgaben auf digitale Weise, indem der Tastgrad der Welle (ein Signal, das zyklisch zwischen hohem und niedrigem Pegel wechselt) angepasst wird.

Für Arduino sind die digitalen Ausgangsports LOW und HIGH, die jeweils 0V und 5V entsprechen. Allgemein definieren wir LOW als 0 und HIGH als 1. Arduino gibt innerhalb von 1 Sekunde 500 Signale mit 0 oder 1 aus. Wenn sie „1“ sind, wird 5V ausgegeben. Umgekehrt, wenn sie alle 0 sind, beträgt die Ausgabe 0V. Oder wenn sie 010101010101... sind, beträgt der durchschnittliche Ausgang 2,5V.

Mit anderen Worten beeinflusst das Verhältnis von 0 und 1 die Spannung, je mehr 0- und 1-Signale pro Zeiteinheit ausgegeben werden, desto genauer ist die Steuerung.

Die GPIO34, 35, 36 und 39 des ESP32 können kein PWM verwenden.

![](media/A18.png)

**3. Schaltplan**

![](media/A19.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. Testergebnis**

Nach dem Hochladen des Codes sehen wir, wie die LED langsam heller und dunkler wird, genau wie der Rhythmus des Atmens.