### Progetto 16 Timebomb

**1. Descrizione**

Questo progetto ti offrirà l'opportunità di sperimentare un interessante gioco della bomba a tempo.

In questo progetto, la matrice di punti rappresenta la tua bomba a tempo, mentre il tubo digitale mostra il tempo rimanente. I pulsanti non solo controllano la bomba ma permettono anche di impostarne il tempo. Puoi impostare un conto alla rovescia per controllare questa bomba, che esplode quando il conto alla rovescia termina. Inoltre, è adottato un buzzer per l'allarme.

In ogni caso, programmando su più sensori, la tua capacità complessiva di pensiero logico può essere migliorata.

**2. Diagramma di flusso**

![](media/B1.png)

**3. Schema di collegamento**

![](media/B2.png)

**4. Codice di test**

1. Trascina i due blocchi base.

![](media/B3.png)

2. Imposta il pin del pulsante su “input”.

![](media/B4.png)

3. Aggiungi un blocco "init matrix display" da "Matrix" e imposta il pin CS su IO15. A seguire, un blocco "brightness" con valore 3 e un blocco "variable" (imposta il tipo variabile su int e il nome su item, assegnando 0 come valore iniziale).

![](media/B5.png)

4. In "Matrix", trascina un blocco "fill color" e seleziona "black" (cioè spegni tutti i LED per cancellare la visualizzazione precedente). Aggiungi un blocco "display image" per definire una faccina sorridente. Poi, inserisci un blocco refresh per aggiornare il display.

![](media/B6.png)

5. Trascina un blocco "if" e riempi la casella condizione con "interface IO33 button was be pushed?". Aggiungi un blocco "variable mode" dopo "then" e imposta il nome su item e la modalità su "++".

![](media/B7.png)

6. Ripeti l’operazione del passo 5, ma imposta l’interfaccia su IO32 e la modalità su "--".

![](media/B8.png)

7. Trascina un blocco "if" per verificare se il pin IO26 è premuto. In questo "if", aggiungi un blocco repeat e imposta la condizione su "item" = 0.

Nel ciclo "repeat until", inserisci un blocco "variable mode" e imposta "item" su "--", come mostrato sotto. Trascina un blocco "TM1650 display" da "Digital tube" e definisci la stringa mostrata come il blocco "variable item". Poi aggiungi un blocco "buzzer output" e imposta l’uscita su HIGH al pin IO27 seguito da un ritardo di 0.5s. Ripeti l’ultima procedura ma imposta l’uscita su LOW.

![](media/B9.png)

8. Programma un altro ciclo e definisci la condizione come "interface IO25 button was be pushed?". Le esecuzioni seguenti sono in questo ciclo. Inserisci un blocco "TM1650 display" e definisci la stringa mostrata come il blocco "variable item". Poi ripeti il passo 4 ma qui imposta l’immagine su una faccina che piange.

![](media/B10.png)

9. Trascina un blocco "if then" e riempi lo spazio vuoto con la condizione: item ＞ 9999. Aggiungi un’istruzione "set item variable by 0" in questo blocco condizione.

![](media/B11.png)

10. Trascina un blocco "TM1650 display" da "Digital tube" e definisci la stringa mostrata come "variable item". Per lo stesso motivo, non dimenticare un ritardo di 0.2s.

![](media/B12.png)

**Codice completo:**

![](media/B13.png)

**5. Risultato del test**

Dopo aver collegato i fili e caricato il codice, premi il pulsante blu per aggiungere tempo, il verde per ridurre e il rosso per resettare. Premi il pulsante giallo per avviare il conto alla rovescia. Quando termina, la bomba esplode.