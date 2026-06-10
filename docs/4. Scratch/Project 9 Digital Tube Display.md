### Projet 9 Affichage à Tube Numérique

**1. Description**

Cet affichage à tube 4 chiffres est un dispositif utilisé pour afficher un comptage ou l'heure, capable d’afficher des chiffres de 0 à 9 ainsi que des lettres simples. Il est composé de quatre tubes numériques, chacun comportant sept diodes électroluminescentes (LED).

De plus, plusieurs fonctions peuvent être réalisées en connectant leurs broches à la carte de développement Arduino, telles que la gestion du temps et certains jeux stockés.

**2. Principe de Fonctionnement**

![](media/A96.png)

Le TM1650 utilise le protocole IIC et adopte deux lignes de bus (SDA et SCL).

Le code est fourni dans nos blocs, et le tube numérique affichera les chiffres via ce code.

**3. Schéma de Câblage**

![](media/A97.png)

**4. Code de Test**

Pour afficher des chiffres sur l’écran, il suffit de glisser un bloc "TM 1650 display" depuis "Digital tube" et de définir la chaîne de caractères sur 9999.

![](media/A98.png)

**5. Résultat du Test**

Après avoir connecté le câblage et téléchargé le code, l’affichage à tube numérique montre "9999", comme illustré ci-dessous.

![](media/A99.png)

**6. Code Étendu**

Passons à des opérations plus complexes. Plutôt que des chiffres statiques, nous allons afficher des chiffres dynamiques.

Le code suivant manipule les tubes pour afficher de 1 à 9999.

1. Glissez les deux blocs de code de base.

![](media/A100.png)

2. Glissez le bloc suivant depuis "Variables". Définissez le type sur int et nommez-le item, en lui assignant 0 comme valeur initiale.

![](media/A101.png)

3. Glissez le bloc suivant depuis "Control" et réglez-le pour 9999 répétitions.

![](media/A102.png)

4. Glissez un "mode variable" depuis "Variables", définissez son nom sur item et réglez le mode sur "++".

5. Glissez un bloc "TM 1650 display" depuis "Digital tube" et remplacez la valeur de chaîne par la variable item. Ajoutez un délai de 0,5 s après.

![](media/A103.png)

6. Ajoutez un bloc "set variable" après le bloc "repeat". Réinitialisez la variable item à 0. Sinon, la valeur de item dépassera la plage d’affichage après 9999 boucles.

![](media/A104.png)

**Code Complet :**

![](media/A105.png)

**7. Explication du Code**

1. Définissez la chaîne à afficher. Tapez directement les chiffres ou lettres que vous souhaitez afficher dans le champ vide.

![](media/A106.png)

2. Activez ou désactivez ce tube numérique TM 1650. Chaque tube peut être contrôlé séparément.

![](media/A107.png)

3. Il est possible d’effacer l’affichage ou d’utiliser ce bloc comme interrupteur principal pour allumer ou éteindre le tube numérique.

![](media/A108.png)