### Progetto 28 Cancello Intelligente

**1. Descrizione**

Il cancello intelligente è un sistema di parcheggio intelligente che integra MCU e sensore a ultrasuoni, il quale controlla automaticamente il cancello in base alla distanza delle auto, per gestire meglio l’accesso dei veicoli.

Quando viene raggiunta una certa distanza, la MCU riceve il segnale dal sensore e stima la distanza tramite l’intensità del segnale. Se l’auto si sta avvicinando o allontanando, la MCU aprirà o chiuderà il cancello tramite un servo.

**2. Diagramma di flusso**

![](media/B110.png)

**3. Schema di collegamento**

![](media/B111.png)

**4. Codice di test**

Definire una variabile "distance" con l’assegnazione del valore di distanza rilevato dal modulo a ultrasuoni.

Successivamente, confrontare il valore di distanza con 30cm. Se è inferiore a 30cm, il servo ruoterà a 180° per 5s. Altrimenti, il servo tornerà a 0°.

![](media/B112.png)

**5. Risultato del test**

Dopo aver collegato i cavi e caricato il codice, il servo ruoterà a 180° per 5s se la distanza rilevata è inferiore a 30cm. Al contrario, il servo ruoterà a 0°.