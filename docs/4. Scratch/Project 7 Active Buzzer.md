### Projet 7 Buzzer Actif

**1. Description**

Un buzzer actif est un composant utilisé comme alarme, rappel ou dispositif de divertissement, qui produit un son fiable.

De plus, il permet de générer des sons hautement contrôlables, rendant nos projets plus intéressants.

**2. Principe de fonctionnement**

![](media/A82.png)

Un buzzer actif intègre un multivibrateur, il produit donc un son uniquement via une tension continue. La broche 1 du buzzer est connectée à VCC et la broche 2 est contrôlée par un triode. Lorsqu’un niveau haut est appliqué à la base (broche 1) du triode, son collecteur (broche 3) et son émetteur (broche 2) sont reliés à la masse, et le buzzer émet un son.

Inversement, si un niveau bas est appliqué à la base, les autres broches seront déconnectées, donc le buzzer restera silencieux.

**3. Schéma de câblage**

![](media/A83.png)

**4. Code de test**

Si la carte de développement sort un niveau haut, le buzzer émettra un son. S’il sort un niveau bas, le buzzer cessera de sonner.

1. Faites glisser les deux blocs de code de base.

![](media/A84.png)

2. Faites glisser les blocs suivants depuis la partie "Buzzer" et réglez la broche IO5 sur HIGH. Puis réglez le temps de délai à 1s.

![](media/A85.png)

3. Faites glisser les blocs suivants depuis la partie "Buzzer" et réglez la broche IO5 sur LOW. Puis réglez le temps de délai à 1s.

![](media/A86.png)

**Code complet :**

![](media/A87.png)

**5. Résultat du test**

Après avoir téléversé le code et mis sous tension, le buzzer émet un son pendant 1s puis reste silencieux pendant 1s.

**6. Explication du code**

Bloc de sortie du buzzer. Nous définissons d’abord la broche sur IO5 puis réglons la sortie sur "HIGH" ou "LOW". Le buzzer émettra un bip lorsqu’il est à HIGH, tandis qu’il restera silencieux à LOW.

![](media/A88.png)