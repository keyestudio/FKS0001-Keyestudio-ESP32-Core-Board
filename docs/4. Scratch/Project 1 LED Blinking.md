### Progetto 1 Lampeggio LED

**1. Descrizione**

Il lampeggio del LED è un progetto semplice pensato per principianti. È sufficiente installare un LED sulla scheda Arduino e caricare il codice sull'IDE Arduino. Questo progetto rafforza l'apprendimento del framework concettuale di Arduino e l'uso dei metodi per principianti.

**2. Principio di Funzionamento**

![](media/A7.png)

**LED:** In generale, le porte IO con corrente di uscita limitata possono causare una bassa luminosità del LED, quindi nel circuito viene utilizzato un transistor NPN (Q2) come interruttore. In questo caso, il LED si accende se la base (pin 1) del transistor è a livello alto. Al contrario, il LED si spegne quando la base è a livello basso.

**Interruttore a transistor:** In breve, il LED si accende quando la base (pin 1) è a livello alto. Allo stesso tempo, il collettore (pin 3) e l'emettitore (pin 2) sono collegati, e quindi VCC passa attraverso una resistenza di limitazione della corrente al LED e infine a GND, formando un circuito. Al contrario, il LED si spegne quando la base è a livello basso. In questa condizione, collettore ed emettitore sono scollegati e il LED si spegne.

**3. Schema di Collegamento**

![](media/A8.png)

**4. Codice di Test**

Secondo i principi precedenti, possiamo controllare il LED tramite i livelli dei pin sulla scheda di sviluppo.

1. Trascina il seguente blocco nella sezione "Events".

![](media/A9.png)

2. Trascina il seguente blocco nella sezione "Control".

![](media/A10.png)

3. Trascina il seguente blocco nella sezione "Pins" e imposta il pin IO5 come output.

   ![](media/A11.png)

4. Trascina il seguente blocco nella sezione "LED" e imposta il pin IO5 su HIGH.

![](media/A12.png)

5. Trascina il seguente blocco nella sezione "Control".

![](media/A13.png)

6. Trascina i seguenti blocchi e imposta il pin IO5 su LOW.

![](media/A14.png)

**Codice Completo：**

![](media/A15.png)

**5. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, il LED si accenderà per 1s e si spegnerà per 1s.

**6. Spiegazione del Codice**

<p style="color:red;">Nota: La modalità del pin deve essere impostata su "output" quando si utilizza il modulo LED.<p>

1. I blocchi di codice non verranno eseguiti se il seguente blocco non è presente.

![](media/A16.png)

2. I blocchi di codice nel seguente blocco verranno eseguiti in loop.

![](media/A17.png)

3. È un modulo utilizzato per impostare la modalità del pin (controlla LED e buzzer per la modalità “output”, e legge il modulo sensore per la modalità “input”).

![](media/A18.png)

4. È un modulo utilizzato per impostare il pin e i livelli ("HIGH" e "LOW").

![](media/A19.png)

5. È un modulo utilizzato per impostare il tempo di ritardo.

![](media/A20.png)