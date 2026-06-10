### Progetto 8 Musicista

**1. Descrizione**

In questo progetto, utilizzeremo un altoparlante con amplificatore di potenza per riprodurre musica. Questo altoparlante non solo può suonare semplici canzoni, ma anche eseguire ciò che desideri. Pertanto, puoi programmare altri codici interessanti nel progetto per ottenere risultati di apprendimento splendidi.

**2. Principio di funzionamento**

![](media/A28.png)

Il segnale elettrico viene immesso dal pin 1 di RP1 (regola l'intensità del segnale, che corrisponde anche al volume del suono).

Dopo l'accoppiamento in C4 e il passaggio attraverso R5, il segnale raggiunge il pin IN- del 8002B, dove viene amplificato operazionalmente e inviato all'altoparlante BEE1.

**Tabella di confronto delle frequenze in C**

|    Nota     | Frequenza(Hz) |      Nota      | Frequenza(Hz) |     Nota     | Frequenza(Hz) |
| :---------: | :-----------: | :------------: | :-----------: | :----------: | :-----------: |
| Bemolle  1  Do |      262      | Naturale  1  Do |      523      | Diesis  1  Do |     1047      |
| Bemolle  2  Re |      294      | Naturale  2  Re |      587      | Diesis  2  Re |     1175      |
| Bemolle  3  Mi |      330      | Naturale  3  Mi |      659      | Diesis  3  Mi |     1319      |
| Bemolle  4  Fa |      349      | Naturale  4  Fa |      698      | Diesis  4  Fa |     1397      |
| Bemolle  5  Sol|      392      | Naturale  5  Sol|      784      | Diesis  5  Sol|     1568      |
| Bemolle  6  La |      440      | Naturale  6  La |      880      | Diesis  6  La |     1760      |
| Bemolle  7  Si |      494      | Naturale  7  Si |      988      | Diesis  7  Si |     1967      |

**3. Schema di collegamento**

![](media/A29.png)

**4. Codice di prova**

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

**5. Risultato del test**

Dopo aver caricato il codice e acceso l'alimentazione, l'amplificatore riproduce ciclicamente toni musicali con frequenze corrispondenti: DO, Re, Mi, Fa, Sol, La, Si.

**Regolazione del volume dell'amplificatore di potenza:**

 **Accanto all'altoparlante c'è un potenziometro. Possiamo regolare il volume dell'altoparlante ruotandolo.** (Nota: Si prega di usare una forza adeguata per regolarlo, per non danneggiare il potenziometro)

![](media/A30.png)

**6. Espansione della conoscenza**

Suoniamo una canzone di compleanno. I collegamenti rimangono invariati.

**Notazione musicale numerica:**

![](media/A31.png)

**Diagramma di confronto tra Bemolle, Naturale e Diesis**

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