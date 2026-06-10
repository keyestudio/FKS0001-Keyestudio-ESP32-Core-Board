### Progetto 13 Mini Lampada

**1. Descrizione**

In questo progetto, controlleremo una lampada tramite Arduino UNO e un pulsante. Quando premiamo il pulsante, lo stato della lampada cambierà (ACCESA o SPENTA).

**2. Principio di Funzionamento**

![](media/A152.png)

Quando il pulsante è rilasciato, una tensione VCC che passa attraverso R29 fornisce un livello alto al terminale S. Quando viene premuto, i pin 1 e 3, pin 2 e 4 sono collegati e la tensione su S1 arriva a GND come livello basso. In questo momento, R29 evita un cortocircuito tra VCC e GND.

**3. Schema di Collegamento**

![](media/A153.png)

**4. Codice di Test**

1. Aggiungi due blocchi base.

![](media/A154.png)

2. Trascina un blocco "baud rate" da “Serial” e impostalo a 9600.

![](media/A155.png)

3. Poi trascina un blocco "print" da “Serial”, digita “Key status:” nel campo vuoto e impostalo su "no-warp".

![](media/A156.png)

4. Imposta il pin IO15 su “input”.

![](media/A157.png)

5. Trascina un altro blocco “Serial print” da “Serial” e imposta la modalità su "warp". Aggiungi un blocco "state value of button" da “Button” e imposta il pin su IO15.

![](media/A158.png)

**Codice Completo:**

![](media/A159.png)

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, apri il monitor seriale e imposta il baud rate a 9600.  
Quando premiamo il pulsante, la porta seriale stampa "Key status: 0"; quando rilasciamo il pulsante, la porta seriale stampa "Key status: 1".

![](media/A160.png)

**6. Espansione della Conoscenza**

Successivamente, controlleremo il LED tramite lo stato dei pulsanti.

**Diagramma di Flusso：**

![](media/A161.png)

**Schema di Collegamento：**

![](media/A162.png)

**Codice:**

1. Trascina due blocchi base.

![](media/A163.png)

2. Imposta il pin del LED su “output” e il pin del pulsante su “input”.

![](media/A164.png)

3. Trascina un blocco "if else" da “Control”. Aggiungi un blocco "button pin" da “Button” dopo "if" e imposta il suo pin su IO15. Metti un blocco "LED output" sotto "if" e impostalo su HIGH, e un altro sotto "else" impostandolo su LOW. I pin del LED sono entrambi su IO4.

![](media/A165.png)

**Codice Completo:**

![](media/A166.png)

**8. Spiegazione del Codice**

**Nota: La modalità pin deve essere impostata su "input" quando si usa il modulo pulsante.**

1. Verifica se il pulsante è premuto. Se sì, questo blocco restituisce true.

![](media/A167.png)

2. Legge il valore del pulsante. Quando il pulsante non è premuto, il valore è 1. Altrimenti, è 0.

![](media/A168.png)

3. Se la condizione nel rombo è vera, viene eseguito il blocco "if". Altrimenti, il programma esegue il blocco "else".

![](media/A169.png)

4. Imposta il baud rate. Assicurati che il baud rate seriale corrisponda a quello del monitor seriale, altrimenti non verrà stampato nulla. I baud rate comunemente usati sono 9600 e 115200, qui impostiamo 9600.

![](media/A170.png)

5. Stampa caratteri sul monitor seriale. Le parole stampate sono quelle digitate nel campo vuoto. Inoltre, sono incluse tre modalità di stampa: warp, no-warp e HEX (esadecimale).

![](media/A171.png)