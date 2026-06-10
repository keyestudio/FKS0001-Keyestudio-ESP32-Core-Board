### Projet 21 LED Contrôlée par le Son

**1. Description**

La LED contrôlée par le son est un dispositif utilisé pour détecter le son afin de contrôler la luminosité de la LED, composé d’une carte Arduino et de quelques composants. Il peut se connecter à plusieurs capteurs tels que des microphones. Il convertit le son en un signal de tension variable reçu par l’Arduino pour contrôler l’allumage et l’extinction de la LED.

**2. Principe de Fonctionnement**

![](media/B54.png)

Lors de la détection d’un son, la membrane électret du microphone vibre, ce qui modifie la capacité et génère une légère variation de tension.

Ensuite, nous utilisons la puce LM386 pour construire un circuit approprié afin d’amplifier le son détecté jusqu’à 200 fois, ce qui peut être ajusté par un potentiomètre. Tournez-le dans le sens des aiguilles d’une montre pour augmenter le facteur d’amplification.

**3. Schéma de Câblage**

![](media/B55.png)

**4. Code de Test**

Trouvez le bloc "read the value" dans “Sound”, et affichez la valeur sonore lue dans le port série. Construisez les blocs comme suit. Faites attention à ne pas ajouter de délai lors de l’utilisation du capteur sonore.

![](media/B56.png)

**5. Résultat du Test**

Après avoir connecté le câblage et téléversé le code, ouvrez le moniteur série et réglez le débit en bauds à 9600, la valeur analogique sera affichée.

![](media/B57.png)

**6. Code d’Extension**

La lumière de couloir courante est un type de lumière contrôlée par le son. Par ailleurs, elle inclut également une photorésistance.

Différemment, ici nous établissons un modèle où une LED est uniquement affectée par le son. Lorsque le volume analogique dépasse 100, la LED s’allume pendant 2 secondes puis s’éteint.

**Organigramme :**

![](media/B58.png)

**Schéma de Câblage :**

![](media/B59.png)

**Code :**

1. Faites glisser deux blocs de base.

2. Faites glisser un bloc "if else", et remplissez l’hexagone avec un bloc item＞100. Réglez la valeur sur "read the value of sound IO33". Si la condition est satisfaite, la LED sort un niveau HIGH sur la broche IO25 avec un délai de 2s ; sinon, elle sort un niveau LOW sur la même broche sans délai.

![](media/B60.png)

**Code Complet :**

![](media/B61.png)

**7. Explication du Code**

Lire la valeur du son en configurant la broche correspondante.

![](media/B62.png)  
### Projet 22 Mesureur de Bruit

**1. Description**

Le mesureur de bruit Arduino traduit le signal sonore en une série de points, qui sont convertis en motifs affichés sur une matrice de points.

**2. Schéma de Câblage**

![](media/B63.png)

**3. Code de Test**

1. Faites glisser les blocs de base et initialisez l’affichage. Réglez la broche CS sur IO15 et la luminosité à 3. Ajoutez ensuite un bloc variable, sélectionnez int et nommez-le "item" avec une affectation initiale de 0.

2. Ajoutez un bloc variable nommé "item". Utilisez une fonction map pour convertir la plage de la valeur sonore lue de 0-4095 à 0-7, en supposant que la valeur maximale du son est 800.

![](media/B64.png)

3. Effacez l’affichage.

4. Programmez une condition. Si la variable item est supérieure à -1, la matrice de points affiche (x0:0  y0:0 x1:1  y1:0) en rouge.

![](media/B65.png)

5. Répétez l’étape 4, mais la condition est que item soit supérieur à 0. Si c’est le cas, les points en (x0:1  y0:0  x1:1  y1:1) s’allument. Par analogie, construisez les blocs de code en vous référant aux coordonnées suivantes.

6. Enfin, rafraîchissez l’affichage.

**Coordonnées de Référence :**

![](media/B66.png)

![](media/B67.png)

**Code Complet :**

![](media/B68.png)

**4. Résultat du Test**

Après avoir connecté le câblage et téléversé le code, le niveau sonore est affiché sur la matrice de points, comme montré ci-dessous.