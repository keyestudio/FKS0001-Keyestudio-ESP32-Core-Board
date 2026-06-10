### Projet 6 Lumière de Flux d'Eau

**1. Description**

Ce projet simple de lumière de flux d'eau vous permet d'apprendre l'assemblage électronique. Dans ce projet, nous contrôlerons des LEDs pour changer de couleur à une vitesse spécifiée via une carte Arduino.

**2. Schéma de Câblage**

![](media/A74.png)

**3. Code de Test**

Une lumière de flux d'eau consiste en un flux d'éclairage LED allant de la gauche vers la droite.

1. Faites glisser les deux blocs de code de base.

![](media/A75.png)

2. Réglez le mode du pin sur « output ».

![](media/A76.png)

3. Faites glisser les blocs suivants de la partie "LED" et réglez le pin IO15 sur LOW, le pin IO12 sur HIGH. Puis réglez le temps de délai à 0,2s.

![](media/A77.png)

4. Faites glisser les blocs suivants de la partie "LED" et réglez le pin IO12 sur LOW, le pin IO13 sur HIGH. Puis réglez le temps de délai à 0,2s.

![](media/A78.png)

5. Faites glisser les blocs suivants de la partie "LED" et réglez le pin IO13 sur LOW, le pin IO14 sur HIGH. Puis réglez le temps de délai à 0,2s.

![](media/A79.png)

6. Faites glisser les blocs suivants de la partie "LED" et réglez le pin IO14 sur LOW, le pin IO15 sur HIGH. Puis réglez le temps de délai à 0,2s.

   ![](media/A80.png)

**Code Complet：**

![](media/A81.png)

**4. Résultat du Test**

Après avoir téléversé le code et mis sous tension, les LEDs s'allument de la gauche vers la droite.