### Projet 21 LED Contrôlée par le Son

**1. Description**

La LED contrôlée par le son est un dispositif utilisé pour détecter le son afin de contrôler la luminosité de la LED, composé d’une carte Arduino et de quelques composants. Il peut se connecter à plusieurs capteurs tels que des microphones. Il convertit le son en un signal de tension variable reçu par l’Arduino pour contrôler l’allumage et l’extinction de la LED.

**2. Principe de Fonctionnement**

![](media/B14.png)

Lors de la détection d’un son, la membrane électret du microphone vibre, ce qui modifie la capacité et génère une légère variation de tension.

Ensuite, nous utilisons la puce LM3 pour construire un circuit adapté afin d’amplifier le son détecté, réglable par un potentiomètre. Tournez-le dans le sens horaire pour augmenter le gain.

**3. Schéma de Câblage**

![](media/B15.png)

**4. Code de Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.1：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33; //Define sound as IO33

void setup()
{
  Serial.begin(9600);
  pinMode(sound,INPUT);
}

void loop()
{
  int value = analogRead(sound);
  Serial.println(value);
}
```

**5. Résultat du Test**

Après avoir connecté le câblage et téléversé le code, ouvrez le moniteur série en réglant le débit à 9600, la valeur analogique s’affichera.

![](media/B16.png)

**Réglage de la sensibilité :**

Si vous trouvez que la sensibilité du capteur sonore est adéquate, vous pouvez ajuster le potentiomètre du capteur sonore (à droite pour la sensibilité maximale, à gauche pour la sensibilité minimale).

![](media/B17.png)

**6. Extension des Connaissances**

La lumière de couloir courante est un type de lumière contrôlée par le son. Par ailleurs, elle inclut aussi une photorésistance. Contrairement à cela, ici nous établissons un modèle où une LED est uniquement affectée par le son. Lorsque le volume analogique dépasse 100, la LED s’allume pendant 2 secondes puis s’éteint.

- **Organigramme :**

![](media/B18.png)

- **Schéma de Câblage :**

![](media/B19.png)

- **Code :**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.2：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33;   //Define sound to IO33
int led = 25;      //Define led to IO25

void setup()
{
  pinMode(led,OUTPUT);   //Set IO25 to output 
}

void loop()
{
  int value = analogRead(sound);    //Read analog value of IO33 and assign it to value
  if(value > 100)
  {                  //Judge whether value is greater than 100
    digitalWrite(led,HIGH);         //If IO25 pin outputs high level, LED lights up
    delay(2000);
  }
  else
  {
    digitalWrite(led,LOW);          //If IO25 pin outputs low level, LED lights off
  }
}
```

- **Résultat du Test**

Lorsque la valeur détectée par le capteur sonore est supérieure à 100, la LED rouge s’allume.