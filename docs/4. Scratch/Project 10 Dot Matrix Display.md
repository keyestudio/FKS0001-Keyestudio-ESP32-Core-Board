### Projet 10 Afficheur Matrice de Points

**1. Description**

Ce module se compose d'une matrice de points LED 8x8 avec une broche de contrôle pour chaque ligne ainsi que chaque colonne afin de régler la luminosité des LED. Connecté à une carte Arduino, la luminosité des LED est contrôlée pour afficher des caractères et des figures via la programmation Arduino. De cette manière, des caractères simples, des chiffres et des figures peuvent être affichés. Il peut également être utilisé dans des machines de jeu ou des écrans.

![](media/A109.png)

Le MAX7219 est un circuit intégré avec communication SPI et peut être utilisé pour contrôler la matrice de points 8x8. La communication SPI du MAX7219 est intégrée dans nos bibliothèques et vous pouvez l'appeler directement.

**2. Schéma de câblage**

![](media/A110.png)

**3. Code de test**

1. Faites glisser les deux blocs de code de base.

![](media/A111.png)

2. Faites glisser un bloc "init matrix display" depuis “Matrix” et réglez CS sur IO15. DIN et CLK sont des broches fixes respectivement sur IO23 et IO18.

![](media/A112.png)

3. Faites glisser un bloc "set brightness" et réglez-le à 3.

![](media/A113.png)

4. Faites glisser un bloc "image" et choisissez l’icône cœur.

![](media/A114.png)

5. Ajoutez un bloc "refresh" à la fin.

![](media/A115.png)

**Code complet :**

![](media/A116.png)

**4. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, un cœur s’affichera sur la matrice de points, comme montré ci-dessous.

![](media/A117.png)

**5. Explication du code**

1. Définir la broche CS. Dans le code, DIN est fixé à IO23 et SLK à IO18, tandis que la broche CS est optionnelle. Pour un câblage pratique, nous sélectionnons IO15.

![](media/A118.png)

2. Dessiner des pixels. Ce bloc de code allume ou éteint les pixels sur la matrice de points selon les axes x et y, avec du rouge pour allumé et du noir pour éteint.

![](media/A119.png)

3. Dessiner une ligne. Localisez la ligne par deux groupes de points de coordonnées, également en rouge pour allumé et noir pour éteint.

![](media/A120.png)

4. Afficher des caractères. Nous avons ajouté des bibliothèques de caractères, vous n’avez donc qu’à taper une lettre pour l’afficher sur la matrice de points. De plus, cela doit être utilisé en coopération avec un bloc "rotation 180°".

![](media/A121.png)

5. Afficher des chiffres. De même, vous n’avez qu’à taper un chiffre pour l’afficher sur la matrice de points, et cela doit aussi être utilisé en coopération avec un bloc "rotation 180°".

![](media/A122.png)

6. Afficher des chaînes de caractères défilantes. En associant un bloc "rotation 180°", les chaînes défilantes spécifiées s’afficheront après réglage de leur vitesse.

![](media/A123.png)

7. Afficher une image. Pour plus de commodité, nous avons déjà intégré quelques icônes d’émotions qui peuvent être sélectionnées directement.

![](media/A124.png)

8. Afficher des couleurs de remplissage. Vous pouvez régler sur noir (LED éteinte) ou rouge (LED allumée).

![](media/A125.png)

9. Rafraîchir l’affichage. La matrice de points doit être rafraîchie si elle affiche quelque chose. Sinon, une erreur peut survenir.

![](media/A126.png)

10. Régler la luminosité. Vous pouvez baisser la luminosité lors du débogage pour éviter de fatiguer vos yeux.

![](media/A127.png)

11. Régler les angles de rotation. Pour une grande compatibilité avec plus de codes, certaines données et icônes nécessitent une rotation afin d’éviter un affichage inversé. C’est pourquoi un bloc "rotation 180°" est nécessaire dans les codes.

![](media/A128.png)