### Projet 7 Buzzer Actif

**1. Description**

Un buzzer actif est un composant utilisé comme alarme, rappel ou dispositif de divertissement, qui produit un son fiable. De plus, il permet de générer des sons hautement contrôlables, rendant nos projets plus intéressants.

**2. Principe de Fonctionnement**

![](media/A26.png)

Un buzzer actif intègre un multi-vibrateur, il produit donc un son uniquement via une tension continue. La broche 1 du buzzer est connectée à VCC et la broche 2 est contrôlée par un triode. Lorsqu’un niveau haut est appliqué à la base (broche 1) du triode, son collecteur (broche 3) et son émetteur (broche 2) sont reliés à la masse (GND), et le buzzer émet un son.

Inversement, si un niveau bas est appliqué à la base, les autres broches sont déconnectées, donc le buzzer reste silencieux.

**3. Schéma de Câblage**

![](media/A27.png)

**4. Code de Test**

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

**5. Résultat du Test**

Après avoir téléversé le code et alimenté le circuit, le buzzer émet un son pendant 1s puis reste silencieux pendant 1s.
