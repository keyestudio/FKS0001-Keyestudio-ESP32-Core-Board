### Projet 8 Interprète Musical

**1. Description**

Dans ce projet, nous utiliserons un haut-parleur amplifié pour jouer de la musique. Ce haut-parleur peut non seulement jouer des chansons simples, mais aussi interpréter ce que vous souhaitez. Ainsi, vous pouvez programmer d'autres codes intéressants dans le projet pour obtenir des résultats d'apprentissage remarquables.

**2. Principe de Fonctionnement**

![](media/A89.png)

Le signal électrique est injecté depuis la broche 1 de RP1 (ajuste l'intensité du signal, ce qui correspond également au volume sonore).  
Après couplage dans C4 et passage par R5, le signal atteint la broche IN- du 8002B, où il est amplifié opérationnellement puis envoyé au haut-parleur BEE1.

**3. Schéma de Câblage**

![](media/A90.png)

**4. Code de Test**

![](media/A91.png)

**5. Résultat du Test**

Après avoir téléversé le code et mis sous tension, l'amplificateur joue en boucle des notes musicales avec les fréquences correspondantes : DO, Ré, Mi, Fa, Sol, La, Si.

**6. Extension des Connaissances**

Faisons-le jouer une chanson d'anniversaire. Nous avons déjà ajouté plusieurs chansons dans la bibliothèque, vous pouvez donc directement glisser ces blocs de chansons depuis "Music".

**Code :**

![](media/A92.png)

**7. Explication du Code**

1. Définir la fréquence de la note. Après avoir configuré la broche, nous pouvons sélectionner la fréquence pour composer la musique.

![](media/A93.png)

2. Module musique, pour faciliter l'utilisation, nous avons intégré 6 morceaux dans le code, ainsi, il suffit de configurer la broche et de sélectionner la musique.

![](media/A94.png)

3. Module arrêt de la lecture, il suffit de configurer la broche correspondante pour arrêter la musique.

![](media/A95.png)