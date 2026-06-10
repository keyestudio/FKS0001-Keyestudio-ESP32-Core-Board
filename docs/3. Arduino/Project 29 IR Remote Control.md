### Progetto 29 Controllo Remoto IR

**1. Descrizione**

Il controllo remoto IR utilizza un segnale IR per controllare il LED, semplificando notevolmente il processo di controllo del LED.

**2. Principio di Funzionamento**

![](media/B41.png)

In questo progetto, utilizziamo spesso un portante di circa 38K per la modulazione.

Il sistema di controllo remoto IR include modulazione, emissione e ricezione. Invia i dati tramite modulazione, migliorando l'efficienza della trasmissione e riducendo il consumo energetico.

Generalmente, la frequenza della modulazione del portante è compresa tra 30kHz e 60kHz (di solito 38kHz). Il duty cycle dell'onda quadra è 1/3, come mostrato sotto, ed è determinato dall'oscillatore a cristallo da 455kHz sul lato trasmittente.

Una divisione intera di frequenza è essenziale per l'oscillatore a cristallo su questo lato, e il coefficiente di frequenza è solitamente valutato a 12. Pertanto, 455kHz÷12≈37.9kHz≈38kHz.

**Schema completo di emissione del portante a 38KH:**

![](media/B42.jpg)

**Frequenza portante:** 38KHz

**Lunghezza d'onda:** 940nm

**Angolo di ricezione:** 90°

**Distanza di controllo:** 6M

**Schema dei pulsanti del telecomando:**

![](media/B43.png)

**3. Schema di Collegamento**

![](media/B44.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 29.1 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

const uint16_t recvPin = 19;  // Pin di ricezione infrarossi
IRrecv irrecv(recvPin);  // Crea un oggetto di classe per la ricezione
decode_results results;   // Crea un oggetto di classe per i risultati della decodifica
long ir_rec;

void setup()
{
  Serial.begin(9600); // Inizializza la porta seriale e imposta il baud rate a 9600
  irrecv.enableIRIn(); // Inizia a ricevere segnali
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value; // assegna il segnale alla variabile ir_rec
    if(ir_rec != 0)
    {		// Previene l'esecuzione ripetuta del codice quando il pulsante è premuto
        Serial.print(ir_rec, HEX); // Stampa la variabile ir_rec in esadecimale
        Serial.println();// A capo
    }
    irrecv.resume(); // Rilascia il telecomando IR e riceve il valore successivo.
  }
} 
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale e impostare il baud rate a 9600.

Premere un pulsante sul telecomando e vedrai il valore in esadecimale.

![](media/B45.png)

**6. Approfondimento**

Successivamente, useremo un telecomando IR per controllare il LED. Premere OK per accendere il LED e premere di nuovo per spegnerlo.

**Schema di Collegamento：**

![](media/B46.png)

**Codice：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 29.2 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

int led = 25;
int led_val = 0;
const uint16_t recvPin = 19;  // Pin di ricezione infrarossi
IRrecv irrecv(recvPin);       // Crea un oggetto di classe per la ricezione
decode_results results;       // Crea un oggetto di classe per i risultati della decodifica
long ir_rec;

void setup() 
{
  Serial.begin(9600);   // Inizializza la porta seriale e imposta il baud rate a 9600
  irrecv.enableIRIn();  // Inizia a ricevere segnali
  pinMode(led, OUTPUT);
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value;      // assegna il segnale alla variabile ir_rec
    if (ir_rec != 0) 
    {           // Previene l'esecuzione ripetuta del codice quando il pulsante è premuto
      if (ir_rec == 0xFF02FD) // Determina se il segnale IR ricevuto proviene dal pulsante OK
      {  
        led_val = !led_val;      // Inverto una variabile. Se il valore iniziale è 0, diventa 1 dopo l'inversione  
        digitalWrite(led, led_val);
      }
    }
    irrecv.resume();  // Rilascia il telecomando IR e riceve il valore successivo.
  }
}
```

**Risultato del Test:** 

Premere OK per accendere il LED e premere di nuovo per spegnerlo.