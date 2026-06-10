### **Projet 13 Mini Lampe**

**1. Description**

Dans ce projet, nous allons contrôler une lampe via Arduino UNO et un bouton. Lorsque nous appuyons sur le bouton, l’état de la lampe change (ALLUMÉ ou ÉTEINT).

**2. Principe de fonctionnement**

![](media/A53.png)

Lorsque le bouton est relâché, une tension VCC passant par R29 fournit un niveau haut pour la borne S. Lorsqu’il est pressé, les broches 1 et 3, 2 et 4 sont connectées et la tension sur S1 arrive à la masse (GND) en niveau bas. À ce moment, R29 évite un court-circuit entre VCC et GND.

**3. Schéma de câblage**

![](media/A54.png)

**4. Code de test**

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
  Serial.begin(9600); //Définir le débit en bauds du port série à 9600 
  pinMode(button, INPUT);  //Connecter la broche du bouton au port digital 8 et la configurer en mode entrée.
}

void loop() 
{
  value = digitalRead(button);//Lire la valeur du bouton 
  Serial.print("Key status:"); //Afficher "Key status:" sur le port série 
  Serial.println(value); //Afficher la variable du bouton sur le port série avec saut de ligne
}
```

**5. Résultat du test**

Après avoir connecté le câblage et téléversé le code, ouvrez le moniteur série et réglez le débit à 9600.  
Lorsque nous appuyons sur le bouton, le port série affiche "Key status: 0" ; lorsque nous le relâchons, il affiche "Key status: 1".

![](media/A55.png)

**6. Extension des connaissances**

Ensuite, nous allons contrôler la LED via l’état des boutons.

- **Organigramme :**

![](media/A56.png)

- **Schéma de câblage :**

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
  // initialiser la broche digitale PIN_LED en sortie.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT);
}

// la fonction loop s’exécute en boucle indéfiniment
void loop() 
{
  if (digitalRead(button) == LOW) {    //Lorsque la valeur du bouton est 0 pour la première fois, un rebond est déclenché, donc un délai de 20ms est appliqué pour vérifier si le bouton est toujours à 0. 
    delay(20);                              //Délai de 20ms
    if (digitalRead(button) == LOW) {   //vérifier si la valeur du bouton est 0
      ledState = !ledState;                 //ledState devient l’inverse de sa valeur initiale, ce qui permet d’allumer ou d’éteindre la LED 
      digitalWrite(led, ledState);
    }
    while (digitalRead(button) == LOW);     //maintenir la boucle tant que le bouton est appuyé, en sortir lorsqu’il est relâché
  }
}
```

- **Résultat du test**

Vous pouvez contrôler l’allumage et l’extinction de la LED rouge avec le bouton rouge.