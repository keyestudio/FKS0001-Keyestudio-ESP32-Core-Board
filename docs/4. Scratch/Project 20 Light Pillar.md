### Projet 20 Pilier de Lumière

**1. Description**

La résistance (inférieure à 1KΩ) de la photorésistance varie en fonction de la lumière, ce qui permet de contrôler la luminosité de la matrice de points. Lors du contrôle, nous connectons cette résistance à une broche analogique de la carte pour surveiller la variation de résistance. De cette manière, la lumière contrôle automatiquement la luminosité de l'affichage.

De plus, la photorésistance est largement utilisée dans notre vie quotidienne. Par exemple, un rideau s'ouvre ou se ferme automatiquement en fonction de l'intensité lumineuse extérieure.

**2. Principe de fonctionnement**

![](media/B43.png)

Lorsqu'il fait totalement sombre, la résistance est égale à 0,2MΩ, et la tension au niveau de la borne signal (point 2) tend vers 0V. Plus la lumière est forte, plus la résistance et la tension seront faibles.

**3. Schéma de câblage**

![](media/B44.png)

**4. Code de test**

La valeur analogique de la photorésistance peut être lue :

1. Faites glisser les deux blocs de base. Placez le bloc de réglage du débit en bauds entre eux et réglez-le à 9600.

2. Ajoutez un bloc "impression série" dans la boucle "pour toujours" avec le mode "warp".

3. Faites glisser un bloc "lire la valeur" depuis “Light” vers le bloc "impression série", et réglez la broche sur IO33.

![](media/B45.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série et réglez le débit en bauds à 9600, la valeur analogique s'affichera, dans une plage de 0 à 4095.

![](media/B46.png)

**6. Code d'extension**

Dans ce projet d'extension, nous utilisons cette photorésistance pour détecter l'intensité lumineuse ambiante. Les deux colonnes centrales sont incluses dans cette expérience pour représenter l'intensité lumineuse. Plus il fait clair, plus les LED allumées seront nombreuses. Cela forme un "pilier de lumière".

**Schéma de câblage :**

![](media/B47.png)

1. Faites glisser les deux blocs de base.

2. Dans "Matrix", initialisez l'affichage matriciel et réglez la broche CS sur IO15. Ajoutez un bloc "réglage de la luminosité" et assignez la valeur 3.

![](media/B48.png)

3. Faites glisser un bloc "variable". Réglez sa portée sur Local, son type sur int et nommez-la light.

![](media/B49.png)

4. Assignez une fonction map à la variable. Ajoutez "lire la valeur de light IO33" depuis "Light" à la valeur de la fonction map, dont la plage va de (0,4095) à (0,7).

![](media/B50.png)

5. Trouvez les blocs suivants dans "Matrix". Effacez d'abord l'affichage, puis dessinez des lignes sur l'affichage aux points (x0:3  y0:0, x1:3  y1: variable light) et (x0:4  y0:0, x1:4  y1: variable light). Enfin, rafraîchissez l'affichage de la matrice.

![](media/B51.png)

**Code complet :**

![](media/B52.png)

**7. Explication du code**

Lire la valeur analogique de la photorésistance en configurant la broche.

![](media/B53.png)