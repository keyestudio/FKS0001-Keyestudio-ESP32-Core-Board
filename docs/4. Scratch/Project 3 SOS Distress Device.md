### Progetto 3 Dispositivo di Soccorso SOS

**1. Descrizione**

Il dispositivo SOS è in grado di emettere segnali di soccorso, che coincidono con il principio del codice Morse. È comodo per le emergenze.

**2. Schema di Collegamento**

![](media/A36.png)

**3. Codice di Test**

Prima di tutto, dobbiamo chiarire come lampeggia la luce di soccorso SOS: il LED lampeggia rapidamente 3 volte per la lettera “S” e lentamente 3 volte per la lettera “O”.

Successivamente, controlliamo il numero di lampeggi e la durata tramite l'istruzione "for" e impostiamo l'intervallo di tempo tra le lettere.

1. Trascina i due blocchi di codice.

![](media/A37.png)

2. Trascina il blocco seguente nella sezione "Pins" e imposta il pin IO5 come output.

![](media/A38.png)

**Lettera "S"**

3. Trascina il blocco seguente dalla sezione "Control" e impostalo a 3 volte, poiché "S" significa lampeggiare 3 volte.

![](media/A39.png)

4. Trascina i blocchi seguenti dalla sezione "LED" e imposta il pin IO5 su HIGH. Poi imposta il tempo di ritardo a 0.15s.

![](media/A40.png)

5. Trascina i blocchi seguenti dalla sezione "LED" e imposta il pin IO5 su LOW. Poi imposta il tempo di ritardo a 0.1s.

![](media/A41.png)

**Lettera O**

6. Riferisciti ai passaggi precedenti per costruire i blocchi di codice seguenti. Modifica l'uscita HIGH con un ritardo di 0.4s e LOW con un ritardo di 0.2s.

![](media/A42.png)

**Lettera S**

7. Ripeti i passaggi 3, 4 e 5.

![](media/A43.png)

8. Aggiungi un ritardo di 5s alla fine, e "SOS" si ripeterà ogni 5s.

   ![](media/A44.png)

**Codice Completo：**

![](media/A45.png)

**4. Risultato del Test**

Dopo aver caricato il codice, il LED lampeggia rispettivamente 3 volte rapidamente e lentamente.