### Progetto 17 Allarme di Invasione

**1. Descrizione**

Questo sistema di allarme di invasione è in grado di rilevare intrusi in case o piccoli uffici e avvisare il proprietario per prendere misure tempestive.

In questo progetto, il sensore monitora una determinata area. Un dispositivo sulla scheda Arduino attiverà il LED per accendersi e il buzzer per emettere un segnale acustico di avviso se viene rilevato un movimento in quella zona. Inoltre, la sua sensibilità è regolabile per una rilevazione più precisa.

In pratica, questo modulo offre praticità, facile installazione e costi contenuti. Oltre a case e uffici, si applica anche a fabbriche, magazzini e mercati, proteggendo in larga misura la sicurezza della proprietà.

**2. Principio di Funzionamento**

![](media/B14.png)

Il corpo umano (37°C) emette sempre raggi infrarossi con una lunghezza d’onda di 10μm, che si avvicina a quella rilevata dal sensore.

Per questo motivo, questo modulo è in grado di rilevare il movimento degli esseri umani. Se presente, il sensore PIR emette un segnale alto per circa 3 secondi, poi torna a segnale basso.

**3. Schema di Collegamento**

![](media/B15.png)

**4. Codice di Test**

1. Aggiungere i due blocchi base e trascinare un blocco "baud rate" da “Serial” tra di essi. Impostare la velocità di trasmissione seriale a 9600.

![](media/B16.png)

2. Aggiungere un blocco "if else". Inserire un blocco "read PIR motion sensor" nel riquadro esagonale e impostare l’interfaccia su IO5, così da determinare se c’è un movimento umano. Aggiungere due blocchi "serial print" dopo "then" e "else" e impostare entrambi i modi su "warp". Se la condizione è soddisfatta, stampare “Someone Invaded”. Altrimenti, stampare “No one”, quindi aggiungere un ritardo di 1s.

![](media/B17.png)

**Codice Completo:**

![](media/B18.png)

**5. Risultato del Test**

Dopo aver collegato i cavi e caricato il codice, aprire il monitor seriale e impostare la velocità a 9600. Quando il sensore rileva un movimento, la porta seriale stampa "Someone Invaded", altrimenti stampa “No One”.

![](media/B19.png)

**6. Codice di Espansione**

Creiamo un allarme di invasione. Quando il sensore PIR rileva un essere umano, il LED si accende e il buzzer emette un suono. Al contrario, il LED si spegne e il buzzer resta silenzioso.

**Diagramma di Flusso：**

![](media/B20.png)

**Schema di Collegamento：**

![](media/B21.png)

**Codice：**

![](media/B22.png)

**7. Spiegazione del Codice**

Quando il PIR rileva movimenti umani, emette un segnale alto. Pertanto, possiamo stabilire se c’è un movimento leggendo il pin della scheda di sviluppo collegato a questo sensore.

![](media/B23.png)