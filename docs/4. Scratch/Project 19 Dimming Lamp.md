### Projet 19  Lampe à intensité variable

**1. Description**

La lampe à intensité variable ajuste la luminosité de la LED via un potentiomètre et un contrôleur Arduino. La luminosité dépend de la valeur de la résistance, qui peut être lue et ajustée en connectant les extrémités du potentiomètre aux broches numériques ou analogiques de la carte.  
De plus, ce système est utilisé pour contrôler la tension ou le courant d'autres appareils tels que les ventilateurs, ampoules et chauffages.

**2. Principe de fonctionnement**

![](media/B32.png)

Essentiellement, le potentiomètre est un composant qui peut modifier la valeur de la résistance. Selon la loi d'Ohm (U=I*R), la résistance influence la tension. Notre potentiomètre est de 10K.

Dans ce projet, la résistance maximale est de 10K. La carte ESP32 divisera également la tension de 3V en 4095 parties (3/4095=0.0007326007326). La tension analogique est obtenue en multipliant la valeur lue par 0.0007326007326.

**3. Schéma de câblage**

![](media/B33.png)

**4. Code de test**

La valeur analogique du potentiomètre peut être lue :

1. Faites glisser les deux blocs de base. Placez le bloc de réglage du débit en bauds entre eux et réglez-le à 9600.

2. Ajoutez un bloc "serial print" dans la boucle "forever", et sélectionnez "warp" comme mode d'impression.

3. Faites glisser un bloc "read the value" depuis “pot” vers le bloc serial print, et réglez la broche sur IO33.

![](media/B34.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série, réglez le débit en bauds à 9600, et la valeur analogique s'affichera dans la plage de 0 à 4095.

![](media/B35.png)

**6. Code d’extension**

Nous allons contrôler la luminosité de la LED via un potentiomètre. Comme nous le savons, cela est influencé par le PWM. Cependant, la plage de la valeur analogique est de 0 à 4095 tandis que celle du PWM est de 0 à 255. Ainsi, une fonction "map(value, fromLow, fromHigh, toLow, toHigh)" est nécessaire.

**Schéma de câblage :**

![](media/B36.png)

1. Faites glisser les deux blocs de base.  
2. Ajoutez un bloc variable et définissez-le en local. Sélectionnez "int" comme type et nommez-le "pot".

![](media/B37.png)

3. Faites glisser une fonction "map" depuis “Data” et placez-la à la position d’assignation. Réglez la valeur de "map" sur "read the value of pot IO33", dont la plage va de (0,4095) à (0,255).

![](media/B38.png)

4. Enfin, ajoutez un bloc "LED analogWrite". Réglez la broche sur IO25 et la valeur analogique sur la variable "pot".

![](media/B39.png)

**Code complet :**

![](media/B40.png)

**7. Explication du code**

1. Fonction **map**. La plage de la valeur analogique peut être convertie de 0-4095 à 0-255.

![](media/B41.png)

2. Lecture de la valeur analogique du potentiomètre en configurant sa broche.

![](media/B42.png)