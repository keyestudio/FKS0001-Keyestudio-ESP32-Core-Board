### Projet 8 Interprète Musical

**1. Description**

Dans ce projet, nous utiliserons un haut-parleur amplifié pour jouer de la musique. Ce haut-parleur peut non seulement jouer des chansons simples, mais aussi interpréter ce que vous souhaitez. Ainsi, vous pouvez programmer d'autres codes intéressants dans le projet pour obtenir des résultats d'apprentissage remarquables.

**2. Principe de fonctionnement**

![](media/A28.png)

Le signal électrique est injecté à la broche 1 de RP1 (ajuste l'intensité du signal, ce qui correspond également au volume sonore).

Après couplage dans C4 et passage par R5, le signal atteint la broche IN- du 8002B, où il est amplifié opérationnellement puis envoyé au haut-parleur BEE1.

**Tableau de comparaison des fréquences en Do**

|    Note     | Fréquence(Hz) |      Note      | Fréquence(Hz) |     Note     | Fréquence(Hz) |
| :---------: | :-----------: | :------------: | :-----------: | :----------: | :-----------: |
| Bémol  1  Do |      262      | Naturel  1  Do |      523      | Dièse  1  Do |     1047      |
| Bémol  2  Ré |      294      | Naturel  2  Ré |      587      | Dièse  2  Ré |     1175      |
| Bémol  3  Mi |      330      | Naturel  3  Mi |      659      | Dièse  3  Mi |     1319      |
| Bémol  4  Fa |      349      | Naturel  4  Fa |      698      | Dièse  4  Fa |     1397      |
| Bémol  5  Sol|      392      | Naturel  5  Sol|      784      | Dièse  5  Sol|     1568      |
| Bémol  6  La |      440      | Naturel  6  La |      880      | Dièse  6  La |     1760      |
| Bémol  7  Si |      494      | Naturel  7  Si |      988      | Dièse  7  Si |     1967      |

**3. Schéma de câblage**

![](media/A29.png)

**4. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 8.1 Music Performer 
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5

void setup() 
{
  pinMode(beeppin, OUTPUT);//Define the IO5 port to output mode 
}

void loop() 
{
  tone(beeppin, 262);//Flat DO plays 500ms
  delay(500);
  tone(beeppin, 294);//Flat Re plays 500ms
  delay(500);
  tone(beeppin, 330);//Flat Mi plays 500ms
  delay(500);
  tone(beeppin, 349);//Flat Fa plays 500ms
  delay(500);
  tone(beeppin, 392);//Flat So plays 500ms
  delay(500);
  tone(beeppin, 440);//Flat La plays 500ms 
  delay(500);
  tone(beeppin, 494);//Flat Si plays 500ms 
  delay(500);
  noTone(beeppin);//Stop for 1s 
  delay(1000);
}
```

**5. Résultat du test**

Après avoir téléversé le code et mis sous tension, l'amplificateur joue en boucle des notes musicales avec les fréquences correspondantes : DO, Ré, Mi, Fa, Sol, La, Si.

**Réglage du volume de l'amplificateur :**

 **Il y a un potentiomètre à côté du haut-parleur. Nous pouvons ajuster le volume du haut-parleur en le tournant.** (Note : Veuillez utiliser une force appropriée pour le régler afin de ne pas endommager le potentiomètre)

![](media/A30.png)

**6. Extension des connaissances**

 Jouons une chanson d'anniversaire. Le câblage reste inchangé.

**Notation musicale chiffrée :**

![](media/A31.png)

**Diagramme comparatif des bémols, naturels et dièses**

![](media/A32.png)

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 8.2 Music Performer
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5
// do、re、mi、fa、so、la、si

int doremi[] = {262, 294, 330, 370, 392, 440, 494,      //Falt 0-6
                523, 587, 659, 698, 784, 880, 988,      //Natural 7-13
                1047,1175,1319,1397,1568,1760,1967};    //Sharp 14-20
int happybirthday[] = {5,5,6,5,8,7,5,5,6,5,9,8,5,5,12,10,8,7,6,11,11,10,8,9,8};   //Find the number in arrey doremi[] according to the numbered musical notation 
int meter[] = {1,1,2,2,2,4, 1,1,2,2,2,4, 1,1,2,2,2,2,2, 1,1,2,2,2,4};    // Beats

void setup() 
{
  pinMode(beeppin, OUTPUT); //Set IO5 pin to output mode 
}

void loop() 
{
  for( int i = 0 ; i <= 24 ;i++)
  {       //i<=24, because there are only 24 tones in this song
    //Use tone()function to generate a waveform in "frequency"
   tone(beeppin, doremi[happybirthday[i] - 1]);
   delay(meter[i] * 200); //Wait for 1000ms
   noTone(beeppin);//Stop singing
  }
}