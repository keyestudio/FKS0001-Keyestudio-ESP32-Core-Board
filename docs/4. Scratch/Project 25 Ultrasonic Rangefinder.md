### Progetto 25 Misuratore di Distanza Ultrasonico

**1. Descrizione**

Questo misuratore di distanza ultrasonico misura la distanza degli ostacoli emettendo onde sonore e poi ricevendo l'eco. Cioè, la distanza non è un valore immediato, ma uno osservato tramite un calcolo teorico della differenza di tempo tra emettitore e ricevitore.

L'ultrasuono è in grado di rilevare la forma degli oggetti, attivare porte automatiche e stimare la velocità di flusso e la pressione.

Inoltre, supporta lavori cooperativi con computer. Di conseguenza, il valore misurato può essere trasmesso ai computer tramite scheda Arduino.

Nella vita quotidiana, è ampiamente utilizzato per motori, servi e LED così come per sistemi (navigazione automatica, controllo e sistemi di monitoraggio della sicurezza).

**2. Principio di Funzionamento**

![](media/B91.png)

Come sappiamo, l'ultrasuono è un tipo di segnale a onde sonore ad alta frequenza non udibile. Simile a un pipistrello, questo modulo misura la distanza degli ostacoli calcolando la differenza di tempo tra emissione dell'onda e ricezione dell'eco.

- **Distanza massima:** 3M

- **Distanza minima:** 5cm

- **Angolo di rilevamento:** ≤15°

**3. Schema di Collegamento**

![](media/B92.png)

**4. Codice di Test**

Nel blocco "forever", costruisci due blocchi "serial print" e trascina un blocco "read distance" da “Ultrasonic”. Imposta il pin trig su IO13 e il pin echo su IO14 entrambi in cm. Non dimenticare un ritardo di 0,5s.

![](media/B93.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, apri il monitor seriale impostando la velocità di trasmissione a 9600, e la porta seriale inizierà a stampare il valore della distanza.

![](media/B94.png)

**6. Approfondimento**

Creiamo un misuratore di distanza.

Visualizziamo i caratteri su LCD 1602. Programmiamo per mostrare "Keyestudio" in (3,0) e “distance:” in (0,1) seguito dal valore della distanza in (9,1).

Quando il valore è inferiore a 100 (o 10), un residuo della terza (o della seconda) cifra rimane ancora. Pertanto, è necessario un giudizio "if" per determinare una certa condizione.

**Schema di Collegamento：**

![](media/B95.png)

**Codice：**

1. Trascina i due blocchi base.

2. In "LCD", inizializza l'LCD. Trascina un blocco “LCD print” e aggiungi la stringa di caratteri “Keyestudio” (può anche essere posizionato fuori dal blocco "forever" poiché questa visualizzazione è fissa). Aggiungi un blocco "variable", imposta il tipo su int e nomina la variabile "distance" con un valore iniziale di 0.

![](media/B96.png)

3. Assegna il valore letto della distanza alla variabile "distance". Imposta l'LCD per stampare “Distance：” seguito dal valore della distanza (e dobbiamo calcolare in anticipo i caratteri visualizzati davanti per impostare il cursore dopo di essi).

![](media/B97.png)

4. Costruisci un blocco per "cancellare il residuo di visualizzazione" quando il numero di cifre visualizzate diminuisce. Prima applichiamo una condizione per verificare se la distanza è inferiore a 100 (o 10). In tal caso, uno spazio verrà stampato nel residuo della terza (o della seconda) cifra per cancellare la visualizzazione precedente. Infine, non dimenticare di aggiungere un ritardo di 0,5s.

![](media/B98.png)

**Codice Completo:**

![](media/B99.png)

**7. Spiegazione del Codice**

Legge la distanza dopo aver impostato il pin trig e il pin echo. L'unità del valore visualizzato è opzionale (cm o pollici).

![](media/B100.png)