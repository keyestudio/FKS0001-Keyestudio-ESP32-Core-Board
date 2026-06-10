### Projet 3 Dispositif de Détresse SOS

**1. Description**

Le dispositif SOS est capable d’émettre des signaux de détresse, ce qui correspond au principe du code Morse. Il est pratique en cas d’urgence.

**2. Schéma de câblage**

![](media/A36.png)

**3. Code de test**

Ce que nous devons d’abord clarifier est la façon dont la lumière de détresse SOS clignote : la LED clignote rapidement 3 fois pour le “S” et lentement 3 fois pour le “O”.

Ensuite, nous contrôlons le nombre de clignotements et la durée via l’instruction "for" et définissons un intervalle de temps entre les lettres.

1. Faites glisser les deux blocs de code.

![](media/A37.png)

2. Faites glisser le bloc suivant dans la partie "Pins" et configurez la broche IO5 en sortie.

![](media/A38.png)

**Lettre "S"**

3. Faites glisser le bloc suivant depuis la partie "Control" et réglez-le sur 3 fois, car "S" signifie clignoter 3 fois.

![](media/A39.png)

4. Faites glisser les blocs suivants depuis la partie "LED" et réglez la broche IO5 sur HIGH. Puis réglez le temps de délai à 0,15 s.

![](media/A40.png)

5. Faites glisser les blocs suivants depuis la partie "LED" et réglez la broche IO5 sur LOW. Puis réglez le temps de délai à 0,1 s.

![](media/A41.png)

**Lettre O**

6. Référez-vous aux étapes précédentes pour construire les blocs de code suivants. Modifiez la sortie HIGH pour un délai de 0,4 s et LOW pour 0,2 s.

![](media/A42.png)

**Lettre S**

7. Répétez les étapes 3, 4 et 5.

![](media/A43.png)

8. Ajoutez un délai de 5 s à la fin, et le "SOS" se répétera toutes les 5 s.

   ![](media/A44.png)

**Code complet :**

![](media/A45.png)

**4. Résultat du test**

Après avoir téléchargé le code, la LED clignote respectivement 3 fois rapidement puis lentement.