### Projet 24 Station Météo

**1. Description**

Cette station météo enregistre la température ambiante et la valeur d'humidité via une carte Arduino et un capteur de température et d'humidité.

De plus, elle permet d'ajuster les valeurs de température et d'humidité en fonction des paramètres environnementaux afin d'obtenir des conditions environnementales confortables.

**2. Schéma de câblage**

![](media/B84.png)

**3. Code de test**

1. Ajoutez deux modules de base. Initialisez le LCD 1602 et allumez le rétroéclairage du LCD 1602 (n'oubliez pas de mettre le LCD en marche). Configurez la broche du dht sur IO26 et le mode sur dht11. Déclarez deux variables int nommées “RH“ et “temp“ à 0.

![](media/B85.png)

2. Assignez la valeur d'humidité à la variable RH, et la valeur de température à la variable temp.

![](media/B86.png)

3. Positionnez l'affichage du LCD à x : 0 et y : 0. Ajoutez le module d'affichage lcd et définissez le texte affiché sur "humidity:". Ajoutez de nouveau le module d'affichage lcd et insérez la variable RH dans la zone blanche.

![](media/B87.png)

4. Répétez l'étape 3, mais positionnez y : 1 et le texte affiché sur “temperature:”, puis ajoutez la variable temp dans la zone blanche.

![](media/B88.png)

**Code complet :**

![](media/B89.png)

**4. Résultat du test**

Après avoir connecté le câblage et téléversé le code, l'affichage LCD détectera directement la valeur d'humidité et de température ambiantes.

![](media/B90.png)