### Progetto 8 Music Performer

**1. Descrizione**

In questo progetto, utilizzeremo un altoparlante con amplificatore di potenza per riprodurre musica. Questo altoparlante non solo può suonare semplici canzoni, ma anche eseguire ciò che desideri. Pertanto, puoi programmare altri codici interessanti nel progetto per ottenere risultati di apprendimento splendidi.

**2. Principio di Funzionamento**

![](media/A89.png)

Il segnale elettrico viene immesso dal pin 1 di RP1 (regola l'intensità del segnale, che corrisponde anche al volume del suono).  
Dopo l'accoppiamento in C4 e il passaggio attraverso R5, il segnale raggiunge il pin IN- del 8002B, dove viene amplificato operazionalmente e inviato all'altoparlante BEE1.

**3. Schema di Collegamento**

![](media/A90.png)

**4. Codice di Test**

![](media/A91.png)

**5. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, l'amplificatore riproduce ciclicamente toni musicali con frequenze corrispondenti: DO, Re, Mi, Fa, So, La, Si.

**6. Espansione della Conoscenza**

Facciamo suonare una canzone di compleanno. Abbiamo già aggiunto alcune canzoni nella libreria, quindi puoi trascinare direttamente questi blocchi di canzoni da "Music".

**Codice:**

![](media/A92.png)

**7. Spiegazione del Codice**

1. Imposta la frequenza del tono. Dopo aver impostato il pin, possiamo selezionare la frequenza per comporre la musica.

![](media/A93.png)

2. Modulo musicale, per comodità d'uso, abbiamo integrato 6 brani nel codice, quindi basta impostare il pin e selezionare la musica.

![](media/A94.png)

3. Modulo di stop, basta impostare il pin corrispondente per fermare la musica.

![](media/A95.png)