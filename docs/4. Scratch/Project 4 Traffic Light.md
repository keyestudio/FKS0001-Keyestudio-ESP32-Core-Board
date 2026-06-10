### Projet 4 Feu de Circulation

**1. Description**

Le module de feu de circulation est un dispositif utilisé pour contrôler le passage des piétons et des véhicules. Il comprend une lumière rouge, une jaune et une verte, qui impliquent différentes consignes.

**Rouge pour Stop :** Les piétons et les véhicules s'arrêtent.

**Jaune pour Prudence :** Les piétons et les véhicules se préparent à s’arrêter. Si la conduite est déjà en cours, la vitesse doit être réduite.

**Vert pour Passage :** Les piétons et les véhicules continuent en respectant le code de la route.

Dans ce projet, vous pouvez utiliser Arduino pour écrire du code afin de contrôler les feux de circulation. Par exemple, définir la durée de chaque feu et l’intervalle entre eux. De plus, vous pouvez également ajouter un minuteur pour changer les couleurs des feux selon un planning.

**2. Schéma de câblage**

![](media/A46.png)

**3. Code de test**

Nous simulons simplement les feux de circulation : la LED verte s’allume pendant 5s, la LED jaune clignote 3 fois, et la LED rouge s’allume pendant 5s. Et nous configurons cela en boucle.

Le clignotement de la LED jaune peut utiliser l’instruction for() que nous avons mentionnée dans le projet 3. Ainsi, il suffit de définir le temps d’allumage pour compléter un cycle de feu.

1. Faites glisser les deux blocs de code.

![](media/A47.png)

2. Réglez le mode du pin sur « output »

![](media/A48.png)

3. Faites glisser les blocs suivants de la partie "LED" et réglez le pin IO27 sur HIGH puis LOW. Ensuite, définissez le délai à 5s.

![](media/A49.png)

4. Faites glisser les blocs suivants de la partie "Control" et réglez le nombre de répétitions à 3, puis réglez le pin IO26 sur HIGH puis LOW. Ensuite, définissez le délai à 0,5s.

![](media/A50.png)

5. Répétez l’étape 3, et réglez le pin sur IO25.

![](media/A51.png)

**Code complet :**

![](media/A52.png)

**4. Résultat du test**

Après avoir téléversé le code, la LED verte s’allumera pendant 5s, la LED jaune clignotera 3 fois, et la LED rouge restera allumée pendant 5s.