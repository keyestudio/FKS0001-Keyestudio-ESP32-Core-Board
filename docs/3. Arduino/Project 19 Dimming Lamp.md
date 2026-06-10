### Progetto 19 Lampada Dimmerabile

**1. Descrizione**

La lampada dimmerabile regola la luminosità del LED tramite un potenziometro e un controller Arduino. La luminosità dipende dal valore di resistenza, che può essere letto e regolato collegando le estremità del potenziometro ai pin digitali o analogici sulla scheda. Inoltre, questo sistema è applicato per controllare la tensione o la corrente di altri dispositivi come ventole, lampadine e riscaldatori.

**2. Principio di Funzionamento**

![](media/B3.png)

![](media/B4.png)

Fondamentalmente, il potenziometro è un elemento che può modificare il valore della resistenza. Secondo la legge di Ohm (U=I*R), la resistenza influisce sulla tensione. Il nostro potenziometro è da 10K.

In questo progetto, la resistenza massima è 10K. La scheda ESP32 dividerà equamente la tensione di 3V in 4095 parti (3/4095=0.0007326007326). La tensione analogica si ottiene moltiplicando il valore letto per 0.0007326007326.

**3. Schema di Collegamento**

![](media/B5.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.1 Dimming Lamp
  http://www.keyestudio.com
*/
int pot = 34;      //Definisci la variabile pot su IO34

void setup() 
{
  // inserisci qui il codice di setup, da eseguire una volta:
  Serial.begin(9600);		//Imposta baud rate a 9600
}

void loop() 
{
  // inserisci qui il codice principale, da eseguire ripetutamente:
  int value = analogRead(pot);	//Leggi io34 e assegna il valore alla variabile value
  Serial.println(value);		//Stampa la variabile value e vai a capo
  delay(200);
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale impostando il baud rate a 9600, e verrà visualizzato il valore analogico, nell’intervallo da 0 a 4095. Ruotando il potenziometro si può modificare il valore analogico.

![](media/B6.png)

**6. Approfondimento**

Controlleremo la luminosità del LED tramite un potenziometro. Come sappiamo, questa è influenzata dal PWM. Tuttavia, l’intervallo del valore analogico è 0-4095 mentre quello del PWM è 0-255. Perciò è necessaria la funzione "map(value, fromLow, fromHigh, toLow, toHigh)".

**Schema di Collegamento：**

![](media/B7.png)

**Codice：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.2 Dimming Lamp
  http://www.keyestudio.com
*/
int led = 25;		//Definisci LED su IO25
int pot = 34;		//Definisci pot su IO34

void setup() 
{
  // inserisci qui il codice di setup, da eseguire una volta:
  pinMode(led,OUTPUT);		//Imposta il pin LED come output
}

void loop() 
{
  // inserisci qui il codice principale, da eseguire ripetutamente:
  int value = analogRead(pot);
  int led_val = map(value,0,4095,0,255);  //Converti l’intervallo del valore analogico del potenziometro in quello necessario  
  analogWrite(led,led_val);
}
```

**7. Risultato del Test**

Dopo che il codice è stato caricato con successo, ruotando il potenziometro si modificherà la luminosità del LED rosso.