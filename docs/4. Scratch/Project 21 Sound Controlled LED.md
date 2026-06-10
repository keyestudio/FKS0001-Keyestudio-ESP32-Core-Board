### Progetto 21 LED Controllato dal Suono

**1. Descrizione**

Il LED controllato dal suono è un dispositivo utilizzato per rilevare il suono in modo da controllare la luminosità del LED, composto da una scheda Arduino e alcuni componenti. Può collegarsi a più sensori come i microfoni. Converte il suono in un segnale di tensione variabile che viene ricevuto da Arduino per controllare l’accensione e lo spegnimento del LED.

**2. Principio di Funzionamento**

![](media/B54.png)

Quando viene rilevato un suono, la pellicola elettrettrica nel microfono vibra, modificando la capacità e generando una sottile variazione di tensione.

Successivamente, utilizziamo il chip LM386 per costruire un circuito adeguato che amplifica il suono rilevato fino a 200 volte, regolabile tramite un potenziometro. Ruotandolo in senso orario si aumenta il fattore di amplificazione.

**3. Schema di Collegamento**

![](media/B55.png)

**4. Codice di Test**

Trova il blocco "leggi il valore" in “Sound” e stampa il valore letto sulla porta seriale. Costruisci i blocchi come segue. Fai attenzione a non aggiungere un delay quando usi il sensore di suono.

![](media/B56.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, apri il monitor seriale impostando il baud rate a 9600; verrà visualizzato il valore analogico.

![](media/B57.png)

**6. Codice di Espansione**

La luce da corridoio comunemente vista è un tipo di luce controllata dal suono. Nel frattempo, include anche una fotoresistenza.

Diversamente da quella, qui creiamo un modello in cui un LED è influenzato solo dal suono. Quando il volume analogico supera 100, il LED si accende per 2 secondi e poi si spegne.

**Diagramma di Flusso：**

![](media/B58.png)

**Schema di Collegamento：**

![](media/B59.png)

**Codice：**

1. Trascina due blocchi base.

2. Trascina un blocco "if else" e riempi l’esagono con un blocco item＞100. Imposta il valore su "leggi il valore del suono IO33". Se la condizione è soddisfatta, il LED emette un livello HIGH sul pin IO25 con un ritardo di 2s; altrimenti, emette un livello LOW sullo stesso pin senza ritardo.

![](media/B60.png)

**Codice Completo:**

![](media/B61.png)

**7. Spiegazione del Codice**

Legge il valore del suono impostando il pin relativo.

![](media/B62.png)  
### Progetto 22 Misuratore di Rumore

**1. Descrizione**

Il misuratore di rumore Arduino rappresenta il segnale sonoro tramite una serie di punti, che vengono convertiti in pattern visualizzati su matrice di punti.

**2. Schema di Collegamento**

![](media/B63.png)

**3. Codice di Test**

1. Trascina i blocchi base e inizializza il display. Imposta il pin CS su IO15 e la luminosità a 3. Poi aggiungi un blocco variabile, seleziona int e chiamalo "item" con assegnazione iniziale 0.

2. Aggiungi un blocco variabile chiamato "item". Usa una funzione map per convertire il valore letto del suono da 0-4095 a 0-7, ipotizzando un valore massimo del suono pari a 800.

![](media/B64.png)

3. Pulisci il display.

4. Programma una condizione. Se la variabile item è maggiore di -1, la matrice di punti visualizza (x0:0  y0:0 x1:1  y1:0) in colore rosso.

![](media/B65.png)

5. Ripeti il passo 4, ma la condizione è che item sia maggiore di 0. In tal caso, si accendono i punti in (x0:1  y0:0  x1:1  y1:1). Per analogia, costruisci i blocchi di codice riferendoti alle coordinate seguenti.

6. Infine, aggiorna il display.

**Coordinate di Riferimento:**

![](media/B66.png)

![](media/B67.png)

**Codice Completo:**

![](media/B68.png)

**4. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, il livello di rumore viene visualizzato sulla matrice di punti, come mostrato di seguito.