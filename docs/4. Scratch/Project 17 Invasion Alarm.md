### Projet 17 Alarme d'Invasion

**1. Description**

Ce système d'alarme d'invasion est capable de détecter les intrus dans les maisons ou les petits bureaux et d'avertir l'hôte afin qu'il prenne des mesures à temps.

Dans ce projet, le capteur surveille une certaine zone. Un dispositif sur la carte Arduino déclenchera l'allumage d'une LED et le buzzer émettra un bip pour avertir en cas de détection de mouvement dans cette zone. De plus, sa sensibilité est réglable pour une détection plus précise.

En pratique, ce module se caractérise par sa praticité, sa facilité d'installation et son faible coût. En plus des maisons et bureaux, il s'applique également aux usines, entrepôts et marchés, ce qui protège dans une large mesure la sécurité des biens.

**2. Principe de Fonctionnement**

![](media/B14.png)

Le corps humain (37°C) émet toujours un rayonnement infrarouge avec une longueur d'onde de 10μm, ce qui est proche de celle détectée par le capteur.

C'est pourquoi ce module est capable de détecter les mouvements humains. En cas de détection, le capteur PIR délivre un niveau haut pendant environ 3 secondes, puis un niveau bas.

**3. Schéma de Câblage**

![](media/B15.png)

**4. Code de Test**

1. Ajoutez les deux blocs de base et glissez un bloc "baud rate" depuis “Serial” entre eux. Réglez la vitesse de transmission série à 9600.

![](media/B16.png)

2. Ajoutez un bloc "if else". Placez un bloc "read PIR motion sensor" dans la case hexagonale et réglez l'interface sur IO5, ce qui permettra de déterminer s'il y a un mouvement humain. Ajoutez deux blocs "serial print" après "then" et "else" et réglez les deux modes sur "warp". Si la condition est remplie, affichez “Someone Invaded”. Sinon, affichez “No one”, puis ajoutez un délai de 1 seconde.

![](media/B17.png)

**Code Complet :**

![](media/B18.png)

**5. Résultat du Test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série et réglez la vitesse à 9600. Lorsque le capteur détecte un mouvement, le port série affiche "Someone Invaded", sinon il affiche “No One”.

![](media/B19.png)

**6. Code d'Extension**

Créons une alarme d'invasion. Lorsque le capteur PIR détecte une présence humaine, la LED s'allume et le buzzer émet un son. À l'inverse, la LED s'éteint et le buzzer reste silencieux.

**Organigramme :**

![](media/B20.png)

**Schéma de Câblage :**

![](media/B21.png)

**Code :**

![](media/B22.png)

**7. Explication du Code**

Lorsque le PIR détecte un mouvement humain, il délivre un niveau haut. Par conséquent, nous pouvons déterminer s'il y a un mouvement en lisant la broche de la carte de développement connectée à ce capteur.

![](media/B23.png)