### Progetto 18 Cuore Pulsante

**1. Descrizione**

In questo progetto, un cuore pulsante sarà mostrato tramite una scheda Arduino, un display a matrice di punti 8X8, una scheda circuito e alcuni componenti elettronici. Tramite programmazione, è possibile controllare la frequenza del battito, la dimensione del cuore e la sua luminosità.

**2. Schema di Collegamento**

![](media/B24.png)

**3. Codice di Test**

1. Trascina i due blocchi base.

2. Inizializza il display a matrice di punti. Imposta il pin CS su IO15 e la luminosità su 3. Inserisci queste due esecuzioni tra i blocchi base.

Le esecuzioni seguenti sono tutte nel blocco "forever".

3. Pulisci il display. Controlla il display per disegnare linee e stabilire il sistema di coordinate e il suo origine come segue. Poi, aggiorna il display per mostrare il cuore più piccolo con un ritardo di 1s.

![](media/B25.png)

![](media/B26.png)

4. Ripeti il passo 3 ma disegna le linee come nell’immagine sottostante per mostrare un cuore più grande.

![](media/B27.png)

![](media/B28.png)

**Codice Completo:**

![](media/B29.png)

**4. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, i due cuori di dimensioni diverse vengono visualizzati alternativamente.

![](media/B30.png)![](media/B31.png)