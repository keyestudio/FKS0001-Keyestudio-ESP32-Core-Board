### Progetto 12 Servo

**1. Descrizione**

Questo servo offre alte prestazioni e alta precisione con un angolo massimo di rotazione di 180°. Pesando solo 9g, è perfettamente adatto a qualsiasi dispositivo mini in molteplici occasioni. Inoltre, gode di un tempo di avvio breve, basso rumore e forte stabilità.

**2. Principio di funzionamento**

**Intervallo angolare:** 180° (360°, 180° e 90°)

**Tensione di alimentazione:** 3.3V o 5V

**Pin:** Tre fili

![](media/A143.png)

**GND:** Messa a terra (marrone)

**VCC:** Un pin rosso che si collega a una alimentazione +5V (3.3V)

**S:** Un pin arancione di segnale controllato tramite segnale PWM

![](media/A144.png)

**Principio di controllo**: L'angolo di rotazione è controllato tramite il duty cycle del PWM. Teoricamente, il ciclo standard del PWM è 20ms (50Hz), quindi la larghezza dell'impulso dovrebbe variare tra 1ms e 2ms. Tuttavia, la larghezza reale dell'impulso raggiunge 0.5ms~2.5ms, corrispondente a 0°～180°. Si noti che, per lo stesso segnale, l'angolo di rotazione può variare tra marche diverse di servo.

**3. Schema di collegamento**

![](media/A145.png)

**4. Codice di test**

1. Trascina i due blocchi base e inserisci un blocco "variabile" tra di essi. Imposta il tipo di variabile su int, il nome su angle e assegna 0 come valore iniziale.

![](media/A146.png)

2. **Il servo ruota gradualmente da 0° a 180°:** 

Aggiungi un blocco di ripetizione e imposta il numero di ripetizioni a 180 (180 angoli). Trascina un blocco "modifica variabile" e un blocco "servo" e inseriscili all'interno del blocco di ripetizione. Nomina la variabile "angle" e seleziona la modalità "++". Imposta il PIN del Servo su IO4 e il grado sulla variabile nominata. Non dimenticare di inserire un ritardo di 15ms.

![](media/A147.png)

3. **Il servo ruota gradualmente da 180° a 0°:** Ripeti il passo 2, ma imposta la modalità della variabile su "--".

![](media/A148.png)

**Codice completo：**

![](media/A149.png)

**5. Risultato del test**

Dopo aver collegato i fili e caricato il codice, il servo inizia a ruotare da 0° a 180° e poi da 180° a 0°.

**6. Spiegazione del codice**

1. Imposta i valori del Servo. Il pin del servo e l'angolo di rotazione possono essere controllati impostando i parametri in questo blocco.

![](media/A150.png)

2. Legge il grado attuale del Servo.

![](media/A151.png)