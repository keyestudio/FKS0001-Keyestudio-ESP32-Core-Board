### Progetto 14 Contatore

**1. Descrizione**

Il contatore a tubo digitale Arduino a 4 bit può registrare numeri da 0 a 9999. Dispone di regolazione della velocità di visualizzazione, modalità di conteggio e funzione di reset. Questo modulo è ampiamente utilizzato in contatori in tempo reale (come il conteggio delle pressioni di un pulsante e la rotazione di un motore DC), giochi e apparecchiature sperimentali.

**2. Diagramma di flusso**

![](media/A172.png)

**3. Schema di collegamento**

![](media/A173.png)

**4. Codice di test**

1. Trascina i due blocchi base.

![](media/A174.png)

2. Imposta il pin del pulsante su “input”.

![](media/A175.png)

3. Inserisci un blocco "variabile". Imposta il tipo di variabile su int e il nome su item. Assegna 0 come valore iniziale.

![](media/A176.png)

4. Trascina un blocco "if" da “Control” (viene eseguito solo quando la condizione è soddisfatta). Metti un blocco “Button pressed” da “Button” nella casella condizione (quella esagonale) e imposta il pin su IO19. Trascina un blocco "modalità variabile" e posizionalo dopo "then", definendolo come "item" e impostando la modalità su "++".

![](media/A177.png)

5. Ripeti il passo 4, ma imposta l’interfaccia su IO18 e la modalità su "– –".

![](media/A178.png)

6. Trascina un altro blocco "if" da “Control” e definisci la condizione "il pulsante dell’interfaccia IO17 è stato premuto?". Metti un blocco di impostazione variabile dopo "then" e imposta la variabile a 0.

![](media/A179.png)

7. Trascina un blocco "if" da “Control”. Trova il blocco "＞" in “Operators” e riempi il campo sinistro con la "variabile item" e quello destro con "9999". Inoltre, metti un blocco di impostazione variabile dopo "then" e imposta la variabile a 0.

![](media/A180.png)

8. Trascina un blocco "TM1650 display" da "Digital tube" e imposta la stringa visualizzata sul blocco "variabile item". Infine, non dimenticare di aggiungere un ritardo di 0,2s.

![](media/A181.png)

**Codice completo:**

![](media/A182.png)

**5. Risultato del test**

Dopo aver collegato i cavi e caricato il codice, premi il pulsante verde per aggiungere 1, quello giallo per sottrarre 1 e quello rosso per resettare.

**6. Spiegazione del codice**

Il blocco **">"** viene usato per il confronto tra due valori. Questi due campi possono essere sostituiti sia da numeri che da variabili.

![](media/A183.png)