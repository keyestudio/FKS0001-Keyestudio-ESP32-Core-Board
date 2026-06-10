### Progetto 10 Display a matrice di punti

**1. Descrizione**

Questo modulo consiste in una matrice di LED 8x8 con un pin di controllo per ogni riga e colonna per regolare la luminosità dei LED. Collegandolo alla scheda Arduino, la luminosità dei LED viene controllata per visualizzare caratteri e figure tramite programmazione Arduino. In questo modo, è possibile visualizzare caratteri semplici, numeri e figure. Può essere applicato anche in macchine da gioco o schermi.

![](media/A109.png)

MAX7219 è un IC con comunicazione SPI e può essere utilizzato per controllare la matrice di punti 8x8. La comunicazione SPI del MAX7219 è integrata nelle nostre librerie e può essere richiamata direttamente.

**2. Schema di collegamento**

![](media/A110.png)

**3. Codice di prova**

1. Trascina i due blocchi di codice base.

![](media/A111.png)

2. Trascina un blocco "init matrix display" da “Matrix” e imposta CS su IO15. DIN e CLK sono pin fissi rispettivamente su IO23 e IO18.

![](media/A112.png)

3. Trascina un blocco "set brightness" e impostalo a 3.

![](media/A113.png)

4. Trascina un blocco "image" e scegli l’icona del cuore.

![](media/A114.png)

5. Aggiungi un blocco "refresh" alla fine.

![](media/A115.png)

**Codice completo：**

![](media/A116.png)

**4. Risultato del test**

Dopo aver collegato i fili e caricato il codice, sul display a matrice di punti verrà mostrato un cuore, come illustrato di seguito.

![](media/A117.png)

**5. Spiegazione del codice**

1. Imposta il pin CS. Nel codice, DIN è fisso su io23 e SLK su io18, mentre il pin CS è opzionale. Per una connessione comoda, selezioniamo io15.

![](media/A118.png)

2. Disegna i pixel. Questo blocco di codice accende o spegne i pixel sulla matrice di punti tramite gli assi x e y, con il rosso per acceso e il nero per spento.

![](media/A119.png)

3. Disegna una linea. Posiziona la linea tramite due gruppi di coordinate, sempre con rosso per acceso e nero per spento.

![](media/A120.png)

4. Mostra caratteri. Abbiamo aggiunto librerie di caratteri, quindi basta digitare una lettera per visualizzarla sulla matrice di punti. Inoltre, deve essere usato in combinazione con un blocco "rotation 180°".

![](media/A121.png)

5. Mostra numeri. Analogamente, basta digitare un numero per visualizzarlo sulla matrice di punti, e deve essere usato in combinazione con un blocco "rotation 180°".

![](media/A122.png)

6. Mostra stringhe di caratteri scorrevoli. Collocando un blocco "rotation 180°", le stringhe scorrevoli specificate verranno visualizzate dopo aver impostato la velocità.

![](media/A123.png)

7. Visualizza immagini. Per comodità, abbiamo già integrato alcune icone emotive che possono essere selezionate direttamente.

![](media/A124.png)

8. Visualizza colori di riempimento. Puoi impostare su nero (LED spento) o rosso (LED acceso).

![](media/A125.png)

9. Aggiorna il display. La matrice di punti deve essere aggiornata se visualizza qualcosa. Altrimenti, potrebbe verificarsi un errore.

![](media/A126.png)

10. Imposta la luminosità. Puoi abbassare la luminosità durante il debug per evitare fastidi agli occhi.

![](media/A127.png)

11. Imposta gli angoli di rotazione. Per una maggiore compatibilità con più codici, alcuni dati e icone necessitano di una rotazione per evitare una visualizzazione invertita. Per questo motivo un blocco "rotation 180°" è necessario nei codici.

![](media/A128.png)