### Projet 16 Bombe à retardement

**1. Description**

Ce projet vous offre l'opportunité de découvrir un jeu de bombe à retardement intéressant.

Dans ce projet, la matrice de points représente votre bombe à retardement, tandis que le tube digital affiche le temps restant. Les boutons permettent non seulement de contrôler la bombe mais aussi de régler son temps. Vous pouvez définir un compte à rebours pour contrôler cette bombe, qui explose lorsque le compte à rebours est terminé. De plus, un buzzer est utilisé pour l'alarme.

Quoi qu'il en soit, en programmant avec plusieurs capteurs, votre capacité globale de raisonnement logique peut être améliorée.

**2. Organigramme**

![](media/B1.png)

**3. Schéma de câblage**

![](media/B2.png)

**4. Code de test**

1. Faites glisser les deux blocs de base.

![](media/B3.png)

2. Réglez la broche du bouton en “input”.

![](media/B4.png)

3. Ajoutez un bloc "init matrix display" depuis "Matrix" et réglez la broche CS sur IO15. Ensuite, ajoutez un bloc "brightness" avec une valeur de 3 et un bloc "variable" (réglez le type de variable sur int et nommez-la item, en lui assignant 0 comme valeur initiale).

![](media/B5.png)

4. Dans "Matrix", faites glisser un bloc "fill color" et sélectionnez "black" (c’est-à-dire que toutes les LED s’éteignent pour effacer l’affichage précédent). Ajoutez un bloc "display image" pour définir un visage souriant. Puis, placez un bloc de rafraîchissement pour renouveler l’affichage.

![](media/B6.png)

5. Faites glisser un bloc "if" et remplissez la condition avec "interface IO33 button was be pushed?". Ajoutez un bloc "variable mode" après "then" et réglez son nom sur item et son mode sur "++".

![](media/B7.png)

6. Répétez l’opération de l’étape 5, mais réglez l’interface sur IO32 et le mode sur "--".

![](media/B8.png)

7. Faites glisser un bloc "if" pour vérifier si la broche IO26 est appuyée. Dans ce "if", ajoutez un bloc repeat et réglez sa condition sur "item" = 0.

Dans la boucle "repeat until", placez un bloc "variable mode" et réglez "item" sur "--", comme montré ci-dessous. Faites glisser un bloc "TM1650 display" depuis "Digital tube" et définissez la chaîne affichée comme le bloc "variable item". Ensuite, ajoutez un bloc "buzzer output" et réglez la sortie sur HIGH à la broche IO27 suivi d’un délai de 0,5 s. Reprenez la dernière procédure mais réglez la sortie sur LOW.

![](media/B9.png)

8. Programmez une autre boucle et définissez la condition comme "interface IO25 button was be pushed?". Les exécutions suivantes se trouvent dans cette boucle. Placez un bloc "TM1650 display" et définissez la chaîne affichée comme le bloc "variable item". Puis répétez l’étape 4 mais ici, réglez l’image sur un visage en pleurs.

![](media/B10.png)

9. Faites glisser un bloc "if then" et remplissez le champ vide avec la condition : item ＞ 9999. Ajoutez une instruction "set item variable by 0" dans ce bloc conditionnel.

![](media/B11.png)

10. Faites glisser un bloc "TM1650 display" depuis "Digital tube" et définissez la chaîne affichée comme "variable item". Pour la même raison, n’oubliez pas de mettre un délai de 0,2 s.

![](media/B12.png)

**Code complet :**

![](media/B13.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, appuyez sur le bouton bleu pour ajouter du temps, sur le vert pour réduire et sur le rouge pour réinitialiser. Appuyez sur le bouton jaune pour lancer le compte à rebours. Lorsque celui-ci est terminé, la bombe explose.