### Projet 18 Cœur Battant

**1. Description**

Dans ce projet, un cœur battant sera présenté via une carte Arduino, un écran matrice de points 8x8, une carte de circuit imprimé et quelques composants électroniques. Grâce à la programmation, vous pouvez contrôler la fréquence des battements, la dimension du cœur et sa luminosité.

**2. Schéma de câblage**

![](media/B24.png)

**3. Code de test**

1. Faites glisser les deux blocs de base.

2. Initialisez l'écran matrice de points. Réglez la broche CS sur IO15 et sa luminosité à 3. Placez ces deux exécutions entre les blocs de base.

Les exécutions suivantes sont toutes dans un bloc "pour toujours".

3. Effacez l'écran. Contrôlez l'affichage pour tracer des lignes et établir le système de coordonnées ainsi que son origine comme suit. Ensuite, rafraîchissez l'écran pour afficher le petit cœur avec un délai de 1s.

![](media/B25.png)

![](media/B26.png)

4. Répétez l'étape 3 mais tracez les lignes comme sur l'image ci-dessous pour afficher un cœur plus grand.

![](media/B27.png)

![](media/B28.png)

**Code complet :**

![](media/B29.png)

**4. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, les deux tailles de cœurs s'affichent alternativement.

![](media/B30.png)![](media/B31.png)