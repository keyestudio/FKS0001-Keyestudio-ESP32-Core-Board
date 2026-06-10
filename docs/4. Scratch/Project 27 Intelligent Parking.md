### Progetto 27 Parcheggio Intelligente

**1. Descrizione**

Questo sistema di parcheggio intelligente rileva e ottimizza la posizione di parcheggio tramite un sensore ad ultrasuoni. Con questo sistema, si evita in larga misura il parcheggio errato.

Per prima cosa, è necessario installare il sensore intorno al parcheggio. Successivamente, rileverà la distanza tra l’auto e i suoi bordi e invierà le informazioni alla scheda di sviluppo per controllare l’auto in modo che si regoli automaticamente alla posizione di parcheggio ottimale.

**2. Diagramma di Flusso**

![](media/B104.png)

**3. Schema di Collegamento**

![](media/B105.png)

**4. Codice di Test**

Assegna il valore della distanza rilevata a una variabile e verifica se è maggiore del valore soglia impostato. In tal caso, si accendono le linee corrispondenti sulla matrice di punti. In questo modo, una distanza può essere indicata accendendo le linee.

**Coordinate di Riferimento:**

![](media/B106.png)

**Codice Completo:**

![](media/B107.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, le linee verranno visualizzate sulla matrice di punti. Se la distanza rilevata è inferiore a 50 cm, ci saranno meno linee.

![](media/B108.png)![](media/B109.png)