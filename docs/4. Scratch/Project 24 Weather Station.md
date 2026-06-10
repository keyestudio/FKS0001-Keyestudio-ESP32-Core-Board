### Progetto 24 Stazione Meteo

**1. Descrizione**

Questa stazione meteo registra la temperatura e l'umidità ambientale tramite una scheda Arduino e un sensore di temperatura e umidità.

Inoltre, permette di regolare i valori di temperatura e umidità in base ai parametri ambientali come metodo per ottenere condizioni ambientali confortevoli.

**2. Schema di Collegamento**

![](media/B84.png)

**3. Codice di Test**

1. Aggiungere due moduli base. Inizializzare l'LCD 1602 e accendere la retroilluminazione dell'LCD 1602 (ricordarsi di impostare l'LCD su ON). Impostare il pin del dht su IO26 e la modalità su dht11. Impostare due variabili int “RH“ e “temp“ a 0.

![](media/B85.png)

2. Assegnare il valore di umidità alla variabile RH e il valore di temperatura alla variabile temp.

![](media/B86.png)

3. Impostare la posizione di visualizzazione dell'LCD su x: 0 e y: 0. Aggiungere il modulo di visualizzazione lcd e impostare il carattere da visualizzare su "humidity:". Aggiungere nuovamente il modulo di visualizzazione lcd e aggiungere la variabile RH nella casella bianca.

![](media/B87.png)

4. Ripetere il passo 3, ma impostare y: 1 e il carattere da visualizzare su “temperature:” e aggiungere la variabile temp nella casella bianca.

![](media/B88.png)

**Codice Completo:**

![](media/B89.png)

**4. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, l'LCD mostrerà direttamente i valori di umidità e temperatura ambientale.

![](media/B90.png)