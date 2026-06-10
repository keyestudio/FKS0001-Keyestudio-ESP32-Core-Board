### Projet 1 Clignotement de LED

**1. Description**

Le clignotement de LED est un projet simple conçu pour les débutants. Il suffit d’installer une LED sur la carte Arduino et de téléverser le code dans l’IDE Arduino. Ce projet renforce l’apprentissage du cadre conceptuel Arduino et des méthodes d’utilisation pour les débutants.

**2. Principe de fonctionnement**

![](media/A16.png)

- **LED :** Le schéma ci-dessus représente le circuit de la LED. En général, le courant de sortie limité des ports IO peut entraîner une faible luminosité de la LED, c’est pourquoi un transistor NPN (Q2) est utilisé dans le circuit comme interrupteur. Dans ce cas, la LED s’allume si la base (broche 1) du transistor est à un niveau haut. À l’inverse, la LED s’éteint lorsque la base est à un niveau bas.

- **Interrupteur transistor :** Pour bien comprendre son principe, des connaissances en électronique sont nécessaires. Pour plus de détails, veuillez consulter les documents par vous-même. En résumé, l’allumage et l’extinction de la LED dépendent des niveaux haut et bas de la base du transistor, qui sont déterminés par la broche de la carte de développement. La LED s’allume lorsque la base (broche 1) est à un niveau haut, et s’éteint lorsque la base est à un niveau bas.

**3. Schéma de câblage :**

![](media/A17.png)

**4. Téléversement du code**

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

**5. Résultat du test**

Après avoir téléversé le code et mis sous tension, la LED s’allumera pendant 1 s puis s’éteindra pendant 1 s.