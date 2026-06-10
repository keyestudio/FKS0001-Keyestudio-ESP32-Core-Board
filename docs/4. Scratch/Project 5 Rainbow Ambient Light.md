### Projet 5 Lumière d'Ambiance Arc-en-Ciel

**1. Description**

La LED 2812RGB est une lumière programmable colorée et onirique, dont la couleur, la luminosité et le rythme sont réglables. Cette lumière d'ambiance arc-en-ciel peut être utilisée comme décoration dynamique à volonté. Ou vous pouvez la contrôler pour qu'elle "danse avec la musique". Important, elle peut être améliorée en alarme. Son capteur intégré détecte l'environnement ambiant pour avertir les utilisateurs en changeant sa couleur, sa luminosité et son rythme.

**2. Principe de Fonctionnement**

![](media/A53.png)

Le protocole de données adopte un mode de communication en code retour à zéro sur une seule ligne. Après la réinitialisation du pixel à la mise sous tension, la borne DIN reçoit les données du contrôleur. Les premières données 24 bits arrivant seront extraites par le premier pixel et envoyées au registre de données interne.

Les données restantes seront amplifiées par un circuit d'amplification et transmises via la sortie DOUT au pixel en cascade suivant.  
En étant transmises à travers les pixels, le signal diminue de 24 bits à chaque fois.

De plus, le pixel adopte une technologie d'auto-formage et de retransmission, de sorte que le nombre de pixels en cascade est uniquement limité par la vitesse de transmission du signal.

**3. Schéma de Câblage**

![](media/A54.png)

**4. Code de Test**

Apprenons à allumer la LED 2812 RGB et à régler ses couleurs.

1. Faites glisser les deux blocs de code.

![](media/A55.png)

2. Faites glisser le bloc suivant depuis la partie "RGB LED" et réglez la broche sur IO15 et le nombre de LED sur 6.

![](media/A56.png)

3. Faites glisser le bloc suivant depuis la partie "RGB LED" et réglez la luminosité à 20.

![](media/A57.png)

4. Faites glisser les blocs suivants et réglez le nombre de LED sur 0, 1, 2, 3, 4 et 5, puis choisissez les couleurs rouge, vert, bleu, jaune, violet et blanc.

![](media/A58.png)

5. Ajoutez le bloc suivant.

![](media/A59.png)

**Code Complet :**

![](media/A60.png)

**5. Résultat du Test**

Après avoir téléchargé le code, connecté le câblage et mis sous tension, la LED s'allumera en différentes couleurs, comme montré ci-dessous :

![](media/A61.png)

**6. Extension des Connaissances**

Dans ce projet d'extension, réalisons un mini spectacle lumineux !

Imbriquez quatre blocs "répéter" et ajoutez un "variable +" dedans, puis remettez les variables correspondantes à 0 à la fin de chaque boucle.

![](media/A62.png)

Placez les trois variables ci-dessus dans le bloc "RGB" afin que ces valeurs de couleur soient contrôlées. Ensuite, ajoutez un module de rafraîchissement.

![](media/A63.png)

Placez le RGB dans un bloc "afficher couleur" pour afficher les couleurs. Et définissez une variable item pour contrôler la LED affichée.

![](media/A64.png)

Le module "pour toujours" est utilisé pour contrôler les LEDs RGB, qui vont cycler de 0 à 5 pour allumer progressivement chaque lumière.

![](media/A65.png)

**Code Complet**

![](media/A66.png)

**7. Explication du Code**

1. Définir le nombre de 2812 RGB. Une broche de la carte de développement peut contrôler plusieurs LEDs 2812 RGB, donc il faut définir le nombre à l'avance et sélectionner la broche connectée.

![](media/A67.png)

2. Régler la luminosité des 2812 RGB. Entrez une valeur de luminosité entre 0 et 255, où 255 est la luminosité maximale.

![](media/A68.png)

3. Ce bloc éteint toutes les LEDs 2812 RGB.

![](media/A69.png)

4. Contrôler l'affichage des 2812 RGB. Nous pouvons remplir les champs pour contrôler la LED allumée et sa couleur après avoir sélectionné la broche. Par exemple, "0 à 0" signifie que seule la première LED s'allume. Après avoir téléchargé le code, la première LED s'allumera dans la couleur définie.

**NOTE :** Les deux champs peuvent aussi être remplis avec des variables, permettant ainsi de créer un spectacle lumineux.

![](media/A70.png)

5. Régler la couleur des 2812 RGB. La couleur affichée peut être modulée par les valeurs de rouge, vert et bleu. Nous pouvons ajouter ce bloc dans les réglages de couleur des 2812 RGB.

![](media/A71.png)

6. Il peut contrôler l'affichage d'une seule LED 2812 RGB en entrant le numéro de la LED à contrôler et en sélectionnant la couleur.

![](media/A72.png)

7. Les 2812 RGB afficheront la couleur définie uniquement après rafraîchissement.

![](media/A73.png)