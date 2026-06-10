### Progetto 22 Misuratore di Rumore

**1. Descrizione**

Il misuratore di rumore Arduino rappresenta il segnale sonoro come una serie di punti, che vengono convertiti in pattern visualizzati sulla matrice di punti.

**2. Schema di Collegamento**

![](media/B63.png)

**3. Codice di Test**

1. Trascina i blocchi base e inizializza il display. Imposta il pin CS su IO15 e la luminosità a 3. Poi aggiungi un blocco variabile, seleziona int e chiamalo "item" con un valore iniziale di 0.

2. Aggiungi un blocco variabile e chiamalo "item". Usa una funzione map per convertire il valore sonoro letto da un intervallo 0-4095 a 0-7, considerando però che il valore massimo ipotetico del suono è 800.

![](media/B64.png)

3. Pulisci il display.

4. Programma una condizione. Se la variabile item è maggiore di -1, la matrice di punti visualizza (x0:0  y0:0 x1:1  y1:0) in colore rosso.

![](media/B65.png)

5. Ripeti il passo 4, ma la condizione è che item sia maggiore di 0. In tal caso, si accendono i punti in (x0:1  y0:0  x1:1  y1:1). Per analogia, costruisci i blocchi di codice facendo riferimento alle coordinate seguenti.

6. Infine, aggiorna il display.

**Coordinate di Riferimento:**

![](media/B66.png)

![](media/B67.png)

**Codice Completo:**

![](media/B68.png)

**4. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, il livello di rumore viene visualizzato sulla matrice di punti, come mostrato di seguito.

![](media/B69.png)![](media/B70.png)![](media/B69.png)![](media/B70.png)