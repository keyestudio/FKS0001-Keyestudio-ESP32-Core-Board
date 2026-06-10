### Progetto 4 Semaforo

**1. Descrizione**

Il modulo semaforo è un dispositivo utilizzato per controllare il percorso di pedoni e veicoli. Include una luce rossa, una gialla e una verde, che implicano diverse istruzioni.

**Rosso per Stop:** Pedoni e veicoli devono fermarsi.

**Giallo per Attenzione:** Pedoni e veicoli devono prepararsi a fermarsi. Se la guida è già in corso, la velocità deve essere ridotta.

**Verde per Procedere:** Pedoni e veicoli possono continuare rispettando il codice della strada.

In questo progetto, puoi usare Arduino per scrivere codice che controlla i semafori. Ad esempio, impostare la durata di ogni luce e l’intervallo di tempo tra di esse. Inoltre, puoi anche aggiungere un timer per modificare i colori delle luci secondo una programmazione.

**2. Schema di Collegamento**

![](media/A46.png)

**3. Codice di Test**

Stimoliamo semplicemente i semafori: il LED verde si accende per 5s, il LED giallo lampeggia 3 volte, e il LED rosso si accende per 5s. Impostiamo questo ciclo in loop.

Il lampeggio del LED giallo può utilizzare l’istruzione for() che abbiamo menzionato nel progetto 3. Quindi, dobbiamo solo impostare il tempo di accensione per completare un ciclo del semaforo.

1. Trascina i due blocchi di codice.

![](media/A47.png)

2. Imposta la modalità del pin su “output”

![](media/A48.png)

3. Trascina i seguenti blocchi dalla sezione "LED" e imposta il pin IO27 su HIGH e poi su LOW. Poi imposta il tempo di delay a 5s.

![](media/A49.png)

4. Trascina i seguenti blocchi dalla sezione "Control" e imposta il numero di ripetizioni a 3, poi imposta il pin IO26 su HIGH e poi su LOW. Imposta il tempo di delay a 0.5s.

![](media/A50.png)

5. Ripeti il passo 3, impostando il pin su IO25.

![](media/A51.png)

**Codice Completo：**

![](media/A52.png)

**4. Risultato del Test**

Dopo aver caricato il codice, il LED verde si accenderà per 5s, il LED giallo lampeggerà 3 volte, e il LED rosso rimarrà acceso per 5s.