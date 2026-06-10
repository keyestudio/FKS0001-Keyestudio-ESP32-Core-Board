### Progetto 4 Semaforo

**1. Descrizione**

Il modulo semaforo è un dispositivo utilizzato per controllare il percorso di pedoni e veicoli. Include una luce rossa, una gialla e una verde, che indicano istruzioni diverse.

**Rosso per Stop:** Pedoni e veicoli devono fermarsi.

**Giallo per Attenzione:** Pedoni e veicoli devono prepararsi a fermarsi. Se la marcia è già in corso, la velocità deve essere ridotta.

**Verde per Procedere:** Pedoni e veicoli possono continuare rispettando il codice della strada.

In questo progetto, puoi usare Arduino per scrivere codice che controlli i semafori. Ad esempio, impostare la durata di ogni luce e l’intervallo di tempo tra di esse. Inoltre, puoi aggiungere un timer per modificare i colori delle luci secondo una programmazione.

**2. Schema di Collegamento**

![](media/A21.png)

**3. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 4 Traffic Light
  http://www.keyestudio.com
*/
int greenPin = 27;   //Green LED connects to IO27
int yellowPin = 26; //Yellow LED connects to IO26
int redPin = 25;   //Red LED connects to IO25

void setup() 
{
  //Set all LED interfaces to output mode
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(redPin, OUTPUT);
}

void loop() 
{
  digitalWrite(greenPin, HIGH); //Light green LED up 
  delay(5000);  //Delay 5s
  digitalWrite(greenPin, LOW); //Turn green LED off 
  for (int i = 1; i <= 3; i++) //Execute for 3 times
  {  
    digitalWrite(yellowPin, HIGH); //Light yellow LED up
    delay(500); //Delay 0.5s
    digitalWrite(yellowPin, LOW); // Turn yellow LED off
    delay(500); //Delay 0.5s
  }
  digitalWrite(redPin, HIGH); //Light red LED up 
  delay(5000);  //Delay 5s 
  digitalWrite(redPin, LOW); //Turn red LED off 

}
```

**4. Risultato del Test**

Dopo aver caricato il codice, il LED verde si accenderà per 5 secondi, il LED giallo lampeggerà 3 volte e il LED rosso si accenderà per 5 secondi, in ciclo continuo.