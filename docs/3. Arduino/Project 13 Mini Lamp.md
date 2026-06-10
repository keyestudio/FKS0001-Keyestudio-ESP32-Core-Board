### **Progetto 13 Mini Lampada**

**1. Descrizione**

In questo progetto, controlleremo una lampada tramite Arduino UNO e un pulsante. Quando premiamo il pulsante, lo stato della lampada cambierà (ACCESA o SPENTA).

**2. Principio di Funzionamento**

![](media/A53.png)

Quando il pulsante è rilasciato, una tensione VCC che passa attraverso R29 fornisce un livello alto al terminale S. Quando viene premuto, i pin 1 e 3, pin 2 e 4 sono collegati e la tensione su S1 arriva a GND come livello basso. In questo momento, R29 evita un cortocircuito tra VCC e GND.

**3. Schema di Collegamento**

![](media/A54.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.1 Mini Lamp
  http://www.keyestudio.com
*/
int button = 15;
int value = 0;

void setup() 
{
  Serial.begin(9600); //Imposta la velocità di trasmissione seriale a 9600 
  pinMode(button, INPUT);  //Collega il pin del pulsante alla porta digitale 8 e impostalo in modalità input.
}

void loop() 
{
  value = digitalRead(button);//Legge il valore del pulsante 
  Serial.print("Key status:"); //Stampa "Key status:" sulla porta seriale 
  Serial.println(value); //Stampa la variabile del pulsante sulla porta seriale e va a capo
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, apri il monitor seriale e imposta la velocità a 9600.  
Quando premiamo il pulsante, la porta seriale stampa "Key status: 0"; quando lo rilasciamo, la porta seriale stampa "Key status: 1".

![](media/A55.png)

**6. Espansione della Conoscenza**

Successivamente, controlleremo il LED tramite lo stato del pulsante.

- **Diagramma di Flusso：**

![](media/A56.png)

- **Schema di Collegamento:**

![](media/A57.png)

- **Codice**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.2 Mini Lamp
  http://www.keyestudio.com
*/
#define led	   4
#define button 15
bool ledState = false;

void setup() 
{
  // inizializza il pin digitale PIN_LED come output.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT);
}

// la funzione loop viene eseguita ripetutamente all'infinito
void loop() 
{
  if (digitalRead(button) == LOW) {    //Quando il valore del pulsante è 0 per la prima volta, si attiva il rimbalzo del pulsante, quindi si ritarda di 20ms per verificare se il pulsante è ancora a 0. 
    delay(20);                              //Ritardo di 20ms
    if (digitalRead(button) == LOW) {   //verifica se il valore del pulsante è 0
      ledState = !ledState;                 //ledState diventa l'inverso del suo valore originale, utile per accendere e spegnere il LED 
      digitalWrite(led, ledState);
    }
    while (digitalRead(button) == LOW);     //mantiene il ciclo while finché il pulsante è premuto, esce quando viene rilasciato
  }
}
```

- **Risultato del Test**

Puoi controllare l'accensione e lo spegnimento del LED rosso tramite il pulsante rosso.