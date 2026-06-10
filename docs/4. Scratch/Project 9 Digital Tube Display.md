### Progetto 9 Display a Tubo Digitale

**1. Descrizione**

Questo display a tubo a 4 cifre è un dispositivo utilizzato per visualizzare conteggi o tempo, in grado di mostrare numeri da 0 a 9 e lettere semplici. È composto da quattro tubi digitali, ognuno dei quali ha sette diodi a emissione luminosa (LED).

Inoltre, possono essere realizzate più funzioni collegando i loro pin alla scheda di sviluppo Arduino, come la misurazione del tempo e alcuni giochi memorizzati.

**2. Principio di Funzionamento**

![](media/A96.png)

TM1650 utilizza il protocollo IIC e adotta due linee bus (SDA e SCL).

Il codice è fornito nei nostri blocchi, e il tubo digitale visualizzerà i numeri tramite questo codice.

**3. Schema di Collegamento**

![](media/A97.png)

**4. Codice di Test**

Per mostrare i numeri sul display, è sufficiente trascinare un blocco "TM 1650 display" da "Digital tube" e impostare la stringa numerica su 9999.

![](media/A98.png)

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, il display a tubo digitale mostra "9999", come mostrato di seguito.

![](media/A99.png)

**6. Codice Esteso**

Passiamo a operazioni più complesse. Invece di numeri statici, lo gestiamo per mostrare numeri dinamici.

Il codice seguente manipola i tubi per visualizzare da 1 a 9999.

1. Trascina i due blocchi di codice base.

![](media/A100.png)

2. Trascina il seguente blocco da "Variables". Imposta il tipo su int e il nome su item, assegnando 0 come valore iniziale.

![](media/A101.png)

3. Trascina il seguente blocco da "Control" e impostalo per 9999 volte.

![](media/A102.png)

4. Trascina una "modalità variabile" da "Variables", definisci il nome come item e imposta la modalità su "++".

5. Trascina un blocco "TM 1650 display" da "Digital tube" e sostituisci il valore stringa con la variabile item. Aggiungi un ritardo di 0,5s dopo di esso.

![](media/A103.png)

6. Aggiungi un blocco "set variable" dopo il blocco "repeat". Imposta la variabile item a 0. Altrimenti, il valore di item uscirà dall'intervallo di visualizzazione dopo 9999 cicli.

![](media/A104.png)

**Codice Completo：**

![](media/A105.png)

**7. Spiegazione del Codice**

1. Imposta la stringa da visualizzare. Digita direttamente i numeri o le lettere che vuoi mostrare nel campo vuoto.

![](media/A106.png)

2. Imposta l'ON o OFF di questo tubo digitale TM 1650. Ogni tubo può essere controllato separatamente.

![](media/A107.png)

3. È possibile cancellare il display o usarlo come interruttore principale per accendere o spegnere il tubo digitale.

![](media/A108.png)