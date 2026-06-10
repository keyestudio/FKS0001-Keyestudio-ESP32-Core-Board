### Progetto 11 LCD

**1. Descrizione**

Arduino I2C 1602 LCD è un dispositivo ausiliario comunemente usato per le schede di sviluppo MCU per collegarsi a sensori esterni e moduli. Presenta uno schermo LCD a 2 linee con caratteri larghi 16 bit e luminosità regolabile. Questo modulo programmabile è comodo per la modifica, visualizzazione e gestione dei dati. Inoltre, può mostrare non solo caratteri e cifre ma anche valori dei sensori, come temperatura, umidità o pressione.

Grazie alla sua versatilità, il display è ampiamente utilizzato in molti settori, inclusi prodotti per la casa intelligente, sistemi di monitoraggio industriale, sistemi di controllo robotico e sistemi elettronici automobilistici.

**2. Principio di Funzionamento**

![](media/A129.png)

Il principio è lo stesso della comunicazione IIC. Le funzioni di base sono state incapsulate in librerie in modo che possano essere richiamate direttamente. Se sei interessato, puoi approfondire i principi di funzionamento sottostanti.

**3. Schema di Collegamento**

![](media/A130.png)

**4. Codice di Test**

1. Trascina i due blocchi di codice base.

![](media/A131.png)

2. Trascina il blocco “init LCD” da “LCD” e imposta l’indirizzo I2C a 0x27.

![](media/A132.png)

3. Trascina il blocco "LCD back light" e impostalo su ON. I caratteri sono difficili da leggere senza retroilluminazione.

![](media/A133.png)

4. Trascina un blocco "LCD cursor position" e imposta x a 3 e y a 0. Aggiungi un blocco "LCD print" e digita “keyestudio” nello spazio vuoto.

![](media/A134.png)

5. Trascina un blocco "LCD cursor position" e imposta x a 2 e y a 1. Aggiungi un blocco "LCD print" e digita “Hello,world!” nello spazio vuoto.

![](media/A135.png)

**Codice Completo：**

![](media/A136.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, accendi l’LCD e verranno visualizzati “Hello, world!” e “keyestudio!” sul display.

Se i caratteri non sono chiari, regola il potenziometro della retroilluminazione con un piccolo cacciavite a taglio.

![](media/A137.png)

**6. Spiegazione del Codice**

1. Imposta l’indirizzo di comunicazione IIC. In questo progetto, l’indirizzo dell’LCD 1602 è 0x27.

![](media/A138.png)

2. Controlla la retroilluminazione dell’LCD. I caratteri visualizzati saranno molto più chiari se la retroilluminazione è attiva.

![](media/A139.png)

3. Imposta la posizione del cursore. Fornisce una posizione precisa tramite gli assi x e y. I valori possibili sono X: 0-15 e Y: 0-1.

![](media/A140.png)

4. Stampa i caratteri sull’LCD. Lo spazio vuoto può essere riempito con caratteri o variabili, comodo per visualizzare i valori provenienti da sensori e moduli.

![](media/A141.png)

5. Fai lampeggiare il cursore nella posizione di visualizzazione. Di default, il cursore è inattivo.

![](media/A142.png)