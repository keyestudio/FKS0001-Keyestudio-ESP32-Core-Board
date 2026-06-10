### Progetto 29 Controllo Remoto IR

**1. Descrizione**

Il telecomando IR utilizza un segnale IR per controllare il LED, semplificando notevolmente il processo di controllo del LED.

**2. Principio di Funzionamento**

![](media/B113.png)

In questo progetto, si utilizza spesso un portante di circa 38K per la modulazione.

Il sistema di controllo remoto IR include modulazione, emissione e ricezione. Invia i dati tramite modulazione, migliorando l'efficienza di trasmissione e riducendo il consumo energetico.

Generalmente, la frequenza della modulazione del portante è compresa tra 30kHz e 60kHz (solitamente 38kHz). Il duty cycle dell'onda quadra è 1/3, come mostrato di seguito, ed è determinato dall'oscillatore a cristallo da 455kHz sul lato trasmittente.  
Una divisione di frequenza intera è essenziale per l'oscillatore a cristallo su questo lato, e il coefficiente di frequenza è solitamente valutato a 12. Pertanto, 455kHz÷12≈37.9kHz≈38kHz.

Diagramma completo di emissione del portante a 38KHz:

![](media/B114.jpg)

- **Frequenza portante:** 38KHz

- **Lunghezza d'onda:** 940nm

- **Angolo di ricezione:** 90°

- **Distanza di controllo:** 6M

**Schema dei pulsanti del telecomando:**

![](media/B115.png)

**3. Schema di Collegamento**

![](media/B116.png)

**4. Codice di Test**

1. Trascina i due blocchi base.

2. Trova e trascina il blocco "IR remote init" da “IR Remote” e imposta il suo pin su IO19. Aggiungi un blocco "baud rate" da "serial" e impostalo a 9600.

![](media/B117.png)、

3. Trascina un blocco "if" e riempi la sua condizione con "Received data". Solo quando il modulo IR riceve dati, i blocchi di codice dentro "if" verranno eseguiti.

![](media/B118.png)

4. Trascina un altro blocco "if" e imposta la sua condizione su "Read the data ＞ 0". Solo quando questa condizione è soddisfatta, la porta seriale inizia a stampare i dati.

   Questo sensore funziona così velocemente che il codice può essere eseguito due volte o più mentre si premono i pulsanti di controllo. Tuttavia, la seconda volta di un comando uguale invierà un valore 0, quindi un blocco ">" è necessario per evitare duplicazioni.

![](media/B119.png)

5. Aggiungi un blocco "serial print" dopo "then". Imposta la stampa dei dati letti dal modulo "IR remote" in modalità "warp".

![](media/B120.png)

6. Infine, non dimenticare di aggiornare i dati dopo l'esecuzione.

![](media/B121.png)

**Codice Completo:**

![](media/B122.png)

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, apri il monitor seriale e imposta il baud rate a 9600. Premi il pulsante sul telecomando e vedrai il valore in esadecimale.

![](media/B123.png)

**6. Codice di Espansione**

In questo codice di espansione, realizzeremo una luce controllata da un interruttore remoto IR. Premi OK per accendere il LED e premi di nuovo per spegnerlo.

Per realizzare questa operazione ripetibile, la variabile "item" è essenziale in tutto il codice. La prima volta, item = 0 quindi i codici in "else" vengono eseguiti per assegnare 1 come nuovo valore. La seconda volta, quando item = 1, invece, il blocco "if" viene eseguito per riassegnare 0, alternativamente.

**Schema di Collegamento:**

![](media/B124.png)

**Codice:**

![](media/B125.png)

**7. Spiegazione del Codice**

1. Inizializza il modulo IR remote dopo aver impostato il suo pin di ricezione.

![](media/B126.png)

2. Verifica se il sensore ha ricevuto dati. In tal caso, i blocchi di codice correlati verranno eseguiti.

![](media/B127.png)

3. Leggi i dati ricevuti dal controllo remoto IR.

![](media/B128.png)

4. Aggiorna i dati ricevuti dopo ogni esecuzione completa di ricezione.

![](media/B129.png)