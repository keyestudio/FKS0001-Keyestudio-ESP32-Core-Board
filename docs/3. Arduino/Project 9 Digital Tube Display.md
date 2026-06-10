### Projet 9 Affichage à Tube Numérique

**1. Description**

Cet affichage à 4 chiffres est un dispositif utilisé pour afficher un comptage ou l'heure, capable d'afficher des chiffres de 0 à 9 ainsi que des lettres simples. Il se compose de quatre tubes numériques, chacun comportant sept diodes électroluminescentes (LED).

De plus, plusieurs fonctions peuvent être réalisées en connectant leurs broches à la carte de développement Arduino, telles que la gestion du temps et certains jeux stockés.

**2. Principe de Fonctionnement**

![](media/A33.png)

Le TM1650 utilise le protocole IIC et adopte deux lignes de bus (SDA et SCL).

**Commande de Données :** 0x48.  
Cette commande indique au TM1650 d’allumer les tubes numériques plutôt que de scanner les touches.

**Commande d’Affichage :**

![](media/A34.png)

En réalité, il s'agit d'un octet de données avec différents bits représentant différentes fonctions.  
**bit[6:4] :** Définit la luminosité des LED. Notez que 000 indique la luminosité maximale.  
**bit[3] :** Détermine la présence d’un point décimal.  
**bit[0] :** Détermine si l’affichage est allumé.

**Allumage du Tube Numérique**  
Prenons un exemple : luminosité niveau 8 sans point correspond à 0x05.  
Étapes : Signal de démarrage — Envoi de 0x48 — Réception par l’esclave — Envoi de 0x05 — Réception par l’esclave — Signal de fin  
Après l’allumage, il n’est pas nécessaire de renvoyer 0x48 de manière répétée, car la fonction du tube numérique est confirmée.  
De plus, la luminosité et les modes d’affichage peuvent être énumérés avec plusieurs données en une seule fois, ce qui est clair et économise de l’espace.

**Extinction du Tube Numérique**  
Étapes : Signal de démarrage — Envoi de 0x48 — Réception par l’esclave — Envoi de 0x00 — Réception par l’esclave — Signal de fin

**Affichage des Chiffres sur le Tube Numérique**  
Nous indiquons d’abord au TM1650 d’afficher un chiffre sur le tube prédéterminé. Ensuite, le chiffre sera affiché. Ses huit bits correspondent à huit segments, avec 1 pour allumer et 0 pour éteindre. En cas de doute sur la correspondance, vous pouvez allumer bit par bit en boucle.

Par exemple, lorsque le bit 1 est allumé et affiche 8, la donnée est 0x68. S’il y a un point, 8 sera également affiché en envoyant 0x7f.  
Étapes : Signal de démarrage — Envoi de 0x68 — Réception par l’esclave — Envoi de 0x7f — Réception par l’esclave — Signal de fin  
Résultat : 8 est affiché sur le bit 1.

Pour plus de commodité, un tableau des valeurs correspondantes de 0 à 9 peut être créé. Après amélioration, il est possible d’afficher des chiffres, d’ajuster la luminosité, de déplacer le point décimal et les tubes.

**3. Schéma de Câblage**

![](media/A35.png)

**4. Code de Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.1 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
    DigitalTube.displayFloatNum(9999);   //Values or variables added to the parentheses can be displayed through the digital tube 
}
```

**5. Résultat du Test**

Après avoir connecté le câblage et téléchargé le code, l’affichage à tube numérique montre "9999", comme illustré ci-dessous.

![](media/A36.png)

**6. Code Étendu**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.2 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  for(int num=0; num<10000; num++)
  {   //Si num est inférieur à 10000, num augmente de 1 à chaque cycle
    DigitalTube.displayFloatNum(num);   //Les valeurs ou variables dans les parenthèses peuvent être affichées via le tube numérique
    delay(100);
  }
}
```

**7. Résultat du Test**

Après le téléchargement du code, le tube numérique affiche de 1 à 9999 grâce à la boucle "for".