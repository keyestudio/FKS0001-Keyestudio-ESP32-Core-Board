### Progetto 7 Buzzer Attivo

**1. Descrizione**

Un buzzer attivo è un componente utilizzato come allarme, promemoria o dispositivo di intrattenimento, che produce un suono affidabile.

Inoltre, permette di generare suoni altamente controllabili, rendendo i nostri progetti più interessanti.

**2. Principio di Funzionamento**

![](media/A82.png)

Un buzzer attivo integra un multivibratore, quindi emette suono solo tramite tensione DC. Il pin 1 del buzzer si collega a VCC e il pin 2 è controllato da un triode. Quando viene fornito un livello alto alla base (pin 1) del triode, il collettore (pin 3) e l'emettitore (pin 2) si collegano a GND, e il buzzer emette suono.

Al contrario, se forniamo un livello basso alla base, gli altri pin saranno scollegati, quindi il buzzer rimarrà silenzioso.

**3. Schema di Collegamento**

![](media/A83.png)

**4. Codice di Test**

Se la scheda di sviluppo emette un livello alto, il buzzer emetterà suono. Se emette un livello basso, il buzzer smetterà di suonare.

1. Trascina i due blocchi di codice base.

![](media/A84.png)

2. Trascina i seguenti blocchi dalla sezione "Buzzer" e imposta il pin IO5 su HIGH. Poi imposta il tempo di ritardo a 1s.

![](media/A85.png)

3. Trascina i seguenti blocchi dalla sezione "Buzzer" e imposta il pin IO5 su LOW. Poi imposta il tempo di ritardo a 1s.

![](media/A86.png)

**Codice Completo：**

![](media/A87.png)

**5. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, il buzzer emette suono per 1s e rimane silenzioso per 1s.

**6. Spiegazione del Codice**

Blocco di output del buzzer. Prima definiamo il pin su IO5 e poi impostiamo l'uscita su "HIGH" o "LOW". Il buzzer emetterà un beep quando è su HIGH, mentre rimarrà silenzioso su LOW.

![](media/A88.png)