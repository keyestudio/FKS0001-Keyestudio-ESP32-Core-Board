### Projet 2 LED Respirante

**1. Description**

La LED respirante Arduino utilise le PWM programmable intégré pour générer une forme d’onde analogique. Après la mise sous tension, la luminosité de la LED peut être ajustée via le cycle de service de la forme d’onde afin de réaliser l’effet de LED respirante.

De cette manière, la lumière ambiante peut être simulée en modifiant la luminosité de la LED au fil du temps. De plus, la LED respirante peut former une mini lumière colorée pour créer une ambiance tranquille et chaleureuse.

**2. Qu’est-ce que le PWM ?**

Le PWM contrôle la sortie analogique par des moyens numériques, ce qui permet d’ajuster le cycle de service de l’onde (un signal alternant cycliquement entre un niveau haut et un niveau bas).

Pour Arduino, les ports numériques de sortie de tension sont LOW et HIGH, correspondant respectivement à 0V et 5V. En général, on définit LOW comme 0 et HIGH comme 1. Arduino émettra 500 signaux de 0 ou 1 en 1 seconde. Si ce sont des "1", 5V seront émis. À l’inverse, s’ils sont tous à 0, la sortie sera 0V. Ou si le signal est 010101010101..., la sortie moyenne sera de 2,5V.

Autrement dit, le rapport de sortie entre 0 et 1 influence la valeur de la tension, plus il y a de signaux 0 et 1 émis par unité de temps, plus le contrôle sera précis.

![](media/A21.png)

**3. Schéma de câblage**

![](media/A22.png)

**4. Code de test**

Nous utilisons une instruction "for" pour augmenter une variable de 0 à 255, et définissons cette variable comme sortie PWM (analogWrite(pin, value)). Par ailleurs, un temps de délai peut renforcer le contrôle du temps d’éclairage de la LED. Ensuite, nous utilisons une autre instruction "for" pour la diminuer de 255 à 0 avec un délai afin de contrôler le processus d’atténuation de la LED.

1. Faites glisser les deux blocs de code.

![](media/A23.png)

2. Faites glisser le bloc suivant depuis la partie "Variables", et définissez le nom "item" avec une affectation initiale à "0". Placez ce bloc dans le bloc "forever".

![](media/A24.png)

3. Faites glisser le bloc suivant depuis la partie "Contrôle" et réglez-le pour 255 répétitions, qui est la valeur maximale du PWM.

![](media/A25.png)

4. Faites glisser le bloc suivant depuis la partie "Variables", mettez "item" comme variable modifiée et réglez le mode sur "++".

![](media/A26.png)

5. Faites glisser le bloc suivant depuis la partie “LED” et réglez la broche LED sur IO5. Ajoutez ensuite un bloc "variable" à l’intérieur et remplissez-le avec "item".

![](media/A27.png)

6. Faites glisser le bloc suivant depuis la partie "Contrôle" et réglez le temps à 0,01 s, soit 10 ms.

![](media/A28.png)

7. Selon les étapes précédentes, construisez un autre bloc de code avec la seule différence que le mode de la variable est "– –".

![](media/A29.png)

**Code complet :**

![](media/A30.png)

**5. Résultat du test**

Après avoir téléversé le code, on peut voir la LED s’atténuer progressivement. Elle "respire" de manière régulière.

**6. Explication du code**

1. Ce bloc sert à définir la plage d’utilisation de la variable, son type, son nom et sa valeur initiale.

![](media/A31.png)

2. Le nombre de répétitions peut être assigné dans le champ vide de ce bloc de répétition.

![](media/A32.png)

3. Entrez un nom de variable dans le champ vide et sa valeur augmentera de 1 à chaque exécution du code. "++" peut être changé en "– –".

![](media/A33.png)

4. Entrez un nom de variable dans le champ vide et sa valeur diminuera de 1 à chaque exécution du code. "– –" peut être changé en "++".

![](media/A34.png)

5. Il s’agit d’un module de sortie PWM, et la case blanche correspond à la valeur de sortie du PWM.

![](media/A35.png)