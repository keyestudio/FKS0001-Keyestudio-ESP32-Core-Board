### Projet 11 LCD

**1. Description**

L'Arduino I2C 1602 LCD est un dispositif auxiliaire couramment utilisé pour les cartes de développement MCU afin de se connecter à des capteurs et modules externes. Il dispose d'un écran LCD à 2 lignes et 16 caractères de large avec une luminosité réglable. Ce module programmable est pratique pour l'édition, l'affichage et la gestion des données. De plus, il peut afficher non seulement des caractères et des chiffres, mais aussi des valeurs de capteurs, comme la température, l'humidité ou la pression.

Grâce à son utilité, cet affichage est largement utilisé dans de nombreux domaines, y compris les produits domotiques, les systèmes de surveillance industrielle, les systèmes de contrôle robotique et les systèmes électroniques automobiles.

**2. Principe de fonctionnement**

![](media/A129.png)

Il fonctionne selon le même principe que la communication IIC. Les fonctions sous-jacentes ont été encapsulées dans des bibliothèques afin que vous puissiez les appeler directement. Si vous êtes intéressé, vous pouvez approfondir les principes de pilotage sous-jacents.

**3. Schéma de câblage**

![](media/A130.png)

**4. Code de test**

1. Faites glisser les deux blocs de code de base.

![](media/A131.png)

2. Faites glisser le bloc “init LCD” depuis “LCD” et réglez l’adresse I2C à 0x27.

![](media/A132.png)

3. Faites glisser le bloc "LCD back light" et réglez-le sur ON. Les caractères sont difficiles à lire sans rétroéclairage.

![](media/A133.png)

4. Faites glisser un bloc "LCD cursor position" et réglez x à 3 et y à 0. Ajoutez un bloc "LCD print" et tapez “keyestudio” dans le champ vide.

![](media/A134.png)

5. Faites glisser un bloc "LCD cursor position" et réglez x à 2 et y à 1. Ajoutez un bloc "LCD print" et tapez “Hello,world!” dans le champ vide.

![](media/A135.png)

**Code complet :**

![](media/A136.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, allumez le LCD, et “Hello, world!” ainsi que “keyestudio!” s’afficheront sur l’écran.

Si les caractères sont flous, veuillez ajuster le potentiomètre du rétroéclairage avec un petit tournevis plat.

![](media/A137.png)

**6. Explication du code**

1. Définir l’adresse de communication IIC. Dans ce projet, l’adresse du LCD 1602 est 0x27.

![](media/A138.png)

2. Contrôler le rétroéclairage du LCD. Les caractères affichés seront beaucoup plus clairs si le rétroéclairage est activé.

![](media/A139.png)

3. Définir la position du curseur. Elle est précisée par les axes x et y. Les valeurs possibles sont X : 0-15 et Y : 0-1.

![](media/A140.png)

4. Afficher des caractères sur le LCD. Le champ peut être rempli avec des caractères ou des variables, ce qui est pratique pour afficher les valeurs des capteurs et modules.

![](media/A141.png)

5. Faire clignoter le curseur à la position d’affichage. Par défaut, le curseur est inactif.

![](media/A142.png)