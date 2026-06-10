### Projet 29 Télécommande IR

**1. Description**

La télécommande IR utilise un signal IR pour contrôler une LED, ce qui simplifie grandement le processus de contrôle de la LED.

**2. Principe de fonctionnement**

![](media/B113.png)

Dans ce projet, nous utilisons souvent un porteuse d'environ 38K pour la modulation.

Le système de télécommande IR comprend la modulation, l'émission et la réception. Il envoie des données par modulation, ce qui améliore l'efficacité de transmission et réduit la consommation d'énergie.

Généralement, la fréquence de modulation porteuse est comprise entre 30kHz et 60kHz (habituellement 38kHz). Le rapport cyclique de l'onde carrée est de 1/3, comme illustré ci-dessous, ce qui est déterminé par le quartz oscillateur à 455kHz à l'extrémité émettrice.  
Une division de fréquence entière est essentielle pour le quartz oscillateur à cette extrémité, et le coefficient de fréquence est généralement évalué à 12. Par conséquent, 455kHz ÷ 12 ≈ 37,9kHz ≈ 38kHz.

Diagramme d'émission complet de la porteuse 38kHz :

![](media/B114.jpg)

- **Fréquence porteuse :** 38kHz

- **Longueur d'onde :** 940nm

- **Angle de réception :** 90°

- **Distance de contrôle :** 6M

**Schéma des boutons de la télécommande :**

![](media/B115.png)

**3. Schéma de câblage**

![](media/B116.png)

**4. Code de test**

1. Faites glisser les deux blocs de base.

2. Trouvez et faites glisser le bloc "IR remote init" depuis “IR Remote” et réglez sa broche sur IO19. Ajoutez un bloc "baud rate" depuis "serial" et réglez-le à 9600.

![](media/B117.png)、

3. Faites glisser un bloc "if" et remplissez sa condition avec "Received data". Ce n’est que lorsque le module IR reçoit des données que les blocs de code dans "if" s’exécuteront.

![](media/B118.png)

4. Faites glisser un autre bloc "if" et réglez sa condition sur "Read the data ＞ 0". Ce n’est que lorsque cette condition est satisfaite que le port série commence à imprimer les données.

   Ce capteur fonctionne très rapidement, le code peut donc s’exécuter deux fois ou plus lorsque vous appuyez sur les boutons de contrôle. Cependant, la deuxième fois qu’une même commande est envoyée, une valeur de 0 est émise, donc un bloc ">" est nécessaire pour éviter les doublons.

![](media/B119.png)

5. Ajoutez un bloc "serial print" après "then". Réglez-le pour imprimer les données lues depuis le module "IR remote" en mode "warp".

![](media/B120.png)

6. Enfin, n’oubliez pas de rafraîchir les données après l’exécution.

![](media/B121.png)

**Code complet :**

![](media/B122.png)

**5. Résultat du test**

Après avoir connecté le câblage et téléchargé le code, ouvrez le moniteur série et réglez le débit en bauds à 9600. Appuyez sur un bouton de la télécommande, et vous verrez la valeur en hexadécimal.

![](media/B123.png)

**6. Code d’extension**

Dans ce code d’extension, nous allons faire une lumière contrôlée par un interrupteur télécommandé IR. Appuyez sur OK pour allumer la LED et appuyez de nouveau pour l’éteindre.

Pour réaliser cette opération répétable, la variable "item" est essentielle dans tout le code. La première fois, item = 0 donc les codes dans "else" s’exécutent pour lui assigner 1 comme nouvelle valeur. La deuxième fois, lorsque item = 1, le bloc "if" s’exécute pour réassigner 0, alternativement.

**Schéma de câblage :**

![](media/B124.png)

**Code :**

![](media/B125.png)

**7. Explication du code**

1. Initialisez le module télécommande IR après avoir configuré sa broche de réception.

![](media/B126.png)

2. Vérifiez si le capteur a reçu des données. Si oui, les blocs de code associés s’exécutent.

![](media/B127.png)

3. Lisez les données reçues depuis la télécommande IR.

![](media/B128.png)

4. Rafraîchissez les données reçues après chaque exécution complète de réception.

![](media/B129.png)