### Progetto 20 Pilastro di Luce

**1. Descrizione**

La resistenza (inferiore a 1KΩ) della fotoresistenza varia in base alla luce, quindi può controllare la luminosità della matrice di punti. Durante il controllo, colleghiamo questa resistenza a un pin analogico sulla scheda per monitorare la variazione della resistenza. In questo modo, la luce controlla automaticamente la luminosità del display.

Inoltre, la fotoresistenza è ampiamente utilizzata nella vita quotidiana. Ad esempio, una tenda si apre o si chiude automaticamente in base all'intensità della luce esterna.

**2. Principio di Funzionamento**

![](media/B43.png)

Quando è completamente al buio, la resistenza è pari a 0.2MΩ, e la tensione al terminale di segnale (punto 2) si avvicina a 0V. Più la luce è intensa, più la resistenza e la tensione saranno basse.

**3. Schema di Collegamento**

![](media/B44.png)

**4. Codice di Test**

Il valore analogico della fotoresistenza può essere letto:

1. Trascina i due blocchi base. Inserisci il blocco di impostazione della velocità di trasmissione (baud rate) tra di essi e impostalo a 9600.

2. Aggiungi un blocco "serial print" nel ciclo "forever" con modalità "warp".

3. Trascina un blocco "read the value" da “Light” al blocco "serial print" e imposta il pin su IO33.

![](media/B45.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, apri il monitor seriale impostando la velocità a 9600; verrà visualizzato il valore analogico, nell'intervallo da 0 a 4095.

![](media/B46.png)

**6. Codice di Espansione**

In questo progetto di espansione, utilizziamo la fotoresistenza per rilevare l'intensità della luce ambientale. Le due colonne centrali sono incluse in questo esperimento per rappresentare l'intensità luminosa. Più è chiaro, più LED si accenderanno. Questo forma un "pilastro di luce".

**Schema di Collegamento：**

![](media/B47.png)

1. Trascina i due blocchi base.

2. In "Matrix", inizializza il display a matrice di punti e imposta il pin CS su IO15. Aggiungi un blocco "brightness setting" e assegnagli il valore 3.

![](media/B48.png)

3. Trascina un blocco "variable". Imposta il suo ambito su Local, il tipo su int e il nome su light.

![](media/B49.png)

4. Assegna una funzione map alla variabile. Aggiungi "read the value of light IO33" da "Light" al valore della funzione map, con intervallo da (0,4095) a (0,7).

![](media/B50.png)

5. Trova i seguenti blocchi in "Matrix". Pulisci prima il display, poi disegna linee sul display ai punti (x0:3  y0:0, x1:3  y1: variabile light) e (x0:4  y0:0, x1:4  y1: variabile light). Infine aggiorna il display della matrice.

![](media/B51.png)

**Codice Completo:**

![](media/B52.png)

**7. Spiegazione del Codice**

Legge il valore analogico della fotoresistenza impostando il pin.

![](media/B53.png)