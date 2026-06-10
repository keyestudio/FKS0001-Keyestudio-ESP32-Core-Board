### Projet 28 Portail Intelligent

**1. Description**

Le portail intelligent est un système de parking intelligent qui intègre un MCU et un capteur ultrasonique, contrôlant automatiquement le portail en fonction de la distance des véhicules, afin de mieux gérer l'accès des voitures.

Lorsqu'une certaine distance est atteinte, le MCU reçoit le signal du capteur et estime la distance via l'intensité du signal. Si la voiture s'approche ou s'éloigne, le MCU ouvrira ou fermera le portail via un servo.

**2. Organigramme**

![](media/B110.png)

**3. Schéma de câblage**

![](media/B111.png)

**4. Code de test**

Définir une variable "distance" avec l'affectation de la valeur de distance détectée par le module ultrasonique.

Ensuite, comparer la valeur de distance avec 30 cm. Si elle est inférieure à 30 cm, le servo tournera à 180° pendant 5 s. Sinon, le servo reviendra à 0°.

![](media/B112.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, le servo tournera à 180° pendant 5 s si la distance détectée est inférieure à 30 cm. Dans le cas contraire, le servo tournera à 0°.