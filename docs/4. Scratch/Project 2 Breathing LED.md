### Progetto 2 LED Respirante

**1. Descrizione**

Il LED respirante Arduino utilizza il PWM programmabile a bordo per generare un'onda analogica. Dopo l'accensione, la luminosità del LED può essere regolata tramite il duty cycle dell'onda per realizzare l'effetto di LED respirante.

In questo modo, la luce ambientale può essere simulata variando la luminosità del LED nel tempo. Inoltre, il LED respirante può formare una mini luce colorata per creare un ambiente tranquillo e caldo.

**2. Cos'è il PWM?**

Il PWM controlla l'uscita analogica tramite mezzi digitali, permettendo di regolare il duty cycle dell'onda (un segnale che alterna ciclicamente tra livello alto e livello basso).

Per Arduino, le porte digitali di uscita di tensione sono LOW e HIGH, che corrispondono rispettivamente a 0V e 5V. Generalmente, definiamo LOW come 0 e HIGH come 1. Arduino emette 500 segnali di 0 o 1 in 1 secondo. Se sono "1", verranno emessi 5V. Al contrario, se sono tutti 0, l'uscita sarà 0V. Oppure, se sono 010101010101..., l'uscita media sarà 2,5V.

In altre parole, il rapporto tra segnali 0 e 1 influenza il valore di tensione; più segnali 0 e 1 vengono emessi per unità di tempo, più preciso sarà il controllo.

![](media/A21.png)

**3. Schema di Collegamento**

![](media/A22.png)

**4. Codice di Test**

Utilizziamo l'istruzione "for" per incrementare una variabile da 0 a 255, definendo la variabile come uscita PWM (analogWrite(pin, value)). Inoltre, un tempo di ritardo può rafforzare il controllo del tempo di accensione del LED. Successivamente, usiamo un altro ciclo "for" per diminuirla da 255 a 0 con un tempo di ritardo per controllare il processo di attenuazione del LED.

1. Trascina i due blocchi di codice.

![](media/A23.png)

2. Trascina il blocco seguente dalla sezione "Variabili" e definisci il nome come "item" con un'assegnazione iniziale "0". Inserisci questo blocco nel blocco "forever".

![](media/A24.png)

3. Trascina il blocco seguente dalla sezione "Controllo" e impostalo a 255 volte, che è il valore massimo del PWM.

![](media/A25.png)

4. Trascina il blocco seguente dalla sezione "Variabili", imposta "item" come oggetto modificato e il modo su "++".

![](media/A26.png)

5. Trascina il blocco seguente dalla sezione “LED” e imposta il pin LED su IO5. Poi aggiungi un blocco "variabile" al suo interno e inserisci "item" nel campo vuoto.

![](media/A27.png)

6. Trascina il blocco seguente dalla sezione "Controllo" e imposta il tempo a 0,01s, cioè 10ms.

![](media/A28.png)

7. Seguendo i passaggi precedenti, costruisci un altro blocco di codice con l’unica differenza del modo variabile "– –".

![](media/A29.png)

**Codice Completo：**

![](media/A30.png)

**5. Risultato del Test**

Dopo aver caricato il codice, possiamo vedere che il LED si attenua gradualmente. "Respira" in modo uniforme.

**6. Spiegazione del Codice**

1. Questo blocco serve a impostare l’intervallo utilizzabile della variabile, il tipo di variabile, il nome e il valore iniziale.

![](media/A31.png)

2. Il numero di ripetizioni può essere assegnato nel campo vuoto di questo blocco di ripetizione.

![](media/A32.png)

3. Inserisci un nome di variabile nel campo vuoto e il suo valore aumenterà di 1 ogni volta che il codice viene eseguito. "++" può essere modificato in "– –".

![](media/A33.png)

4. Inserisci un nome di variabile nel campo vuoto e il suo valore diminuirà di 1 ogni volta che il codice viene eseguito. "– –" può essere modificato in "++".

![](media/A34.png)

5. Questo è un modulo di uscita PWM, e la casella bianca rappresenta il valore del PWM in uscita.

![](media/A35.png)