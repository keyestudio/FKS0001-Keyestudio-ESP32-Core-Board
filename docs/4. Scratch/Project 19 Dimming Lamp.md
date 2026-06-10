### Progetto 19  Lampada Dimmerabile

**1. Descrizione**

La lampada dimmerabile regola la luminosità del LED tramite un potenziometro e un controller Arduino. La luminosità dipende dal valore della resistenza, che può essere letta e regolata collegando le estremità del potenziometro ai pin digitali o analogici sulla scheda.  
Inoltre, questo sistema è applicato per controllare la tensione o la corrente di altri dispositivi come ventole, lampadine e riscaldatori.

**2. Principio di Funzionamento**

![](media/B32.png)

Fondamentalmente, il potenziometro è un elemento che può modificare il valore della resistenza. Secondo la legge di Ohm (U=I*R), la resistenza influisce sulla tensione. Il nostro potenziometro è da 10K.

In questo progetto, la resistenza massima è 10K. La scheda ESP32 dividerà equamente la tensione di 3V in 4095 parti (3/4095=0.0007326007326). La tensione analogica si ottiene moltiplicando il valore letto per 0.0007326007326.

**3. Schema di Collegamento**

![](media/B33.png)

**4. Codice di Test**

Il valore analogico del potenziometro può essere letto:

1. Trascina i due blocchi base. Inserisci il blocco di impostazione della baud rate tra di essi e impostalo a 9600.

2. Aggiungi un blocco "serial print" nel ciclo "forever" e seleziona "warp" come modalità di stampa.

3. Trascina un blocco "read the value" da “pot” al serial print, e imposta il pin su IO33.

![](media/B34.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, apri il monitor seriale impostando la baud rate a 9600, e il valore analogico verrà visualizzato nell’intervallo da 0 a 4095.

![](media/B35.png)

**6. Codice di Espansione**

Controlleremo la luminosità del LED tramite un potenziometro. Come sappiamo, è influenzata dal PWM. Tuttavia, l’intervallo del valore analogico è 0-4095 mentre quello del PWM è 0-255. Perciò è necessaria una funzione "map(value, fromLow, fromHigh, toLow, toHigh)".

**Schema di Collegamento：**

![](media/B36.png)

1. Trascina i due blocchi base.  
2. Aggiungi un blocco variabile e impostalo come locale. Seleziona "int" come tipo e chiamalo "pot".

![](media/B37.png)

3. Trascina una funzione "map" da “Data” e posizionala nell’assegnazione. Imposta il valore di "map" su "read the value of pot IO33", con intervallo da (0,4095) a (0,255).

![](media/B38.png)

4. Infine aggiungi un blocco "LED analogWrite". Imposta il pin su IO25 e il valore analogico sulla variabile "pot".

![](media/B39.png)

**Codice Completo:**

![](media/B40.png)

**7. Spiegazione del Codice**

1. Funzione **map**. L’intervallo del valore analogico può essere convertito da 0-4095 a 0-255.

![](media/B41.png)

2. Legge il valore analogico del potenziometro impostando il suo pin.

![](media/B42.png)