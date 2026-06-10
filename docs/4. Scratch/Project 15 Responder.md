### Projet 15 Répondeur

**1. Description**

Ce répondeur programmable reçoit et envoie des signaux via une carte de développement Arduino et un groupe de boutons, et il juge la justesse des réponses grâce à une LED. C'est un bon outil pour exercer la capacité de réaction des élèves et attirer leur attention sur les questions. Si la réponse est correcte, le répondant obtient beaucoup de points.

De plus, il simplifie la gestion des attrapeurs de questions par les enseignants et réduit le désordre des réponses. Il peut même stimuler l'intérêt des élèves pour l'apprentissage.

**2. Organigramme**

![](media/A184.png)

**3. Schéma de câblage**

![](media/A185.png)

**4. Code de test**

1. Faites glisser les deux blocs de base et placez un bloc "variable" entre eux. Définissez le type de variable sur int et nommez-la item avec une affectation initiale de 0. Configurez la broche LED en “output” et la broche du bouton en “input”.

![](media/A186.png)

2. Ajoutez un bloc "LED output", définissez sa broche sur IO27 et réglez la sortie sur HIGH.  
3. Faites glisser un bloc "if" et ajoutez la condition "interface IO19 button was be pushed?".

![](media/A187.png)

4. Ajoutez une affectation de variable et quatre blocs LED output sous "then". Parmi eux, nommez la variable "item" avec une affectation de "0", et réglez toutes les sorties sur LOW respectivement aux broches 12, 13, 14 et 27 (Le répondeur fonctionne uniquement lorsque toutes les LED sont éteintes). De même, n'oubliez pas un délai de 0,2 s.

![](media/A188.png)

5. Ajoutez un bloc "repeat until" et réglez le "until" sur "item = 1", comme montré ci-dessous. Lorsque item = 1, la boucle se termine.

![](media/A189.png)

6. Faites glisser un autre bloc "if" et définissez la condition "Interface IO16 button was be pushed?". Ajoutez un bloc "LED output" sous "then" et réglez la sortie sur HIGH à la broche IO12. Ajoutez également un "set item variable by 1" pour sortir de ce bloc conditionnel.

![](media/A190.png)

7. Répétez l’étape 6, mais réglez l’interface sur IO17 et la broche LED sur IO13.

![](media/A191.png)

8. Répétez encore l’étape 6, mais réglez l’interface sur IO18 et la broche LED sur IO14.

![](media/A192.png)

**Code complet :**

![](media/A193.png)

**5. Résultat du test**

Connectez le câblage et téléversez le code. Les réponses des participants ne sont valides que lorsque la LED rouge est éteinte (le bouton rouge est pressé).

Lorsqu'une personne appuie sur son bouton (jaune, vert ou bleu), la LED correspondante ainsi que la LED rouge s’allument. À ce moment, les autres LED ne peuvent pas s’allumer en appuyant sur les boutons. L’action de réponse ne peut être effectuée que lorsque le bouton rouge est pressé à nouveau.

**6. Explication du code**

1. Module de boucle conditionnelle. Lorsque les conditions dans le losange du module sont remplies, la boucle se termine.

![](media/A194.png)

2. Le bloc "=" est utilisé pour vérifier si les deux valeurs sont égales.

![](media/A195.png)