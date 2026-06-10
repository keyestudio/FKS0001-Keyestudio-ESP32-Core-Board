### Projet 23 Tasse Intelligente

**1. Description**

Dans ce projet, nous utilisons principalement la carte de développement Arduino pour créer une tasse intelligente programmable, qui affiche la température du liquide intérieur via un indicateur RGB. Elle peut contrôler la luminosité de la lumière en définissant un seuil de température. Si le seuil est dépassé, la lumière s’éclaircit. Sinon, elle s’assombrit.

La tasse intelligente permet d’aider les utilisateurs à mieux contrôler la température de leur eau potable et à prévenir efficacement la surchauffe ou le gel.

**2. Principe de Fonctionnement**

![](media/B71.png)

Les réglages liés au DHT11 sont fournis par les fabricants, vous n’avez donc qu’à lire et traiter les données dans l’ordre selon son diagramme de séquence.

De plus, les codes correspondants sont emballés dans nos bibliothèques, ce qui vous facilite la configuration des pins et la lecture des valeurs.

**3. Schéma de Câblage**

![](media/B72.png)

**4. Code de Test**

1. Faites glisser deux blocs de base. Ajoutez le module de débit en bauds série et réglez le débit à 9600.

2. Faites glisser le module DHT depuis « Température et humidité » et réglez la pin sur IO26, le mode sur dht11.

![](media/B73.png)

3. Ajoutez un module d’impression série sans retour à la ligne, et réglez l’impression sur « RH: », puis suivez les étapes ci-dessous, et ajoutez un délai de 1s.

**Code Complet :**

![](media/B74.png)

**5. Résultat du Test**

Après avoir connecté le câblage et téléchargé le code, cliquez ![](media/B75.png) pour ouvrir le moniteur série, réglez le débit à 9600, et la valeur de température et d’humidité s’affichera.

![](media/B76.png)

**6. Code d’Extension**

Dans cette expérience d’extension, nous allons réaliser une tasse intelligente capable d’afficher la température du liquide. Nous divisons 100 en quatre parties avec une LED représentant chacune :

- **LED Rouge :** 100-75°C

- **LED Jaune :** 75-50°C

- **LED Verte :** 50-25°C

- **LED Bleue :** 25-0°C

- **Organigramme :**

![](media/B77.png)

**Schéma de Câblage :**

![](media/B78.png)

**Code :**

1. Faites glisser deux blocs de base. Puis réglez les 4 pins des LED en « output », la pin du DHT11 sur IO26, le mode sur dht11 et le nom de la variable sur temp.

![](media/B79.png)

2. Assignez la valeur de température du DHT11 à la variable temp.

![](media/B80.png)

3. Utilisez le bloc "if else" pour juger la variable temp. Si les conditions sont remplies, la LED correspondante s’allume, sinon elle s’éteint.

**Code Complet :**

![](media/B81.png)

**7. Explication du Code**

1. Dans ce bloc de code, le numéro marqué peut être rempli dans le champ vide afin de connecter plusieurs capteurs de température et d’humidité. Après avoir configuré la pin et le mode, la valeur peut être lue. Dans ce projet, nous avons réglé le mode sur DHT11.

![](media/B82.png)

2. Bloc de code de lecture de la température et de l’humidité.

![](media/B83.png)