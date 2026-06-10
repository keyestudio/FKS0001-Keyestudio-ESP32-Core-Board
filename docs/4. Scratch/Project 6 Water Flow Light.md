### Progetto 6 Luce a Flusso d'Acqua

**1. Descrizione**

Questo semplice progetto di luce a flusso d'acqua ti aiuta a imparare il confezionamento elettronico. In questo progetto, controlleremo i LED per cambiare colore a una velocità specificata tramite una scheda Arduino.

**2. Schema di Collegamento**

![](media/A74.png)

**3. Codice di Test**

Una luce a flusso d'acqua consiste in una sequenza di illuminazione dei LED da sinistra a destra.

1. Trascina i due blocchi di codice base.

![](media/A75.png)

2. Imposta la modalità del pin su “output”.

![](media/A76.png)

3. Trascina i seguenti blocchi dalla sezione "LED" e imposta il pin IO15 su LOW, il pin IO12 su HIGH. Poi imposta il tempo di ritardo a 0,2s.

![](media/A77.png)

4. Trascina i seguenti blocchi dalla sezione "LED" e imposta il pin IO12 su LOW, il pin IO13 su HIGH. Poi imposta il tempo di ritardo a 0,2s.

![](media/A78.png)

5. Trascina i seguenti blocchi dalla sezione "LED" e imposta il pin IO13 su LOW, il pin IO14 su HIGH. Poi imposta il tempo di ritardo a 0,2s.

![](media/A79.png)

6. Trascina i seguenti blocchi dalla sezione "LED" e imposta il pin IO14 su LOW, il pin IO15 su HIGH. Poi imposta il tempo di ritardo a 0,2s.

   ![](media/A80.png)

**Codice Completo：**

![](media/A81.png)

**4. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, i LED si accendono da sinistra a destra.