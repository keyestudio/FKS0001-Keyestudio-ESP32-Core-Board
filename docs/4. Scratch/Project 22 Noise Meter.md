### Projet 22 Compteur de Bruit

**1. Description**

Le compteur de bruit Arduino traduit le signal sonore en une série de points, qui sont convertis en motifs affichés sur une matrice de points.

**2. Schéma de câblage**

![](media/B63.png)

**3. Code de test**

1. Faites glisser les blocs de base et initialisez l'affichage. Réglez la broche CS sur IO15 et la luminosité sur 3. Ensuite, ajoutez un bloc variable, sélectionnez int et nommez-le "item" avec une affectation initiale de 0.

2. Ajoutez un bloc variable et nommez-le "item". Utilisez une fonction map pour convertir la plage de valeurs sonores lues de 0-4095 en 0-7, en supposant que la valeur maximale du son est 800.

![](media/B64.png)

3. Effacez l'affichage.

4. Programmez une condition. Si la variable item est supérieure à -1, la matrice de points affiche (x0:0  y0:0 x1:1  y1:0) en rouge.

![](media/B65.png)

5. Répétez l'étape 4, mais la condition est que item soit supérieur à 0. Si c'est le cas, les points en (x0:1  y0:0  x1:1  y1:1) s'allument. Par analogie, construisez les blocs de code en vous référant aux coordonnées suivantes.

6. Enfin, rafraîchissez l'affichage.

**Coordonnées de référence :**

![](media/B66.png)

![](media/B67.png)

**Code complet :**

![](media/B68.png)

**4. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, le niveau de bruit s'affiche sur la matrice de points, comme illustré ci-dessous.

![](media/B69.png)![](media/B70.png)![](media/B69.png)![](media/B70.png)