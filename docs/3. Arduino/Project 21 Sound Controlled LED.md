### Progetto 21 LED Controllato dal Suono

**1. Descrizione**

Il LED controllato dal suono è un dispositivo utilizzato per rilevare il suono in modo da controllare la luminosità del LED, composto da una scheda Arduino e alcuni componenti. Può collegarsi a più sensori come i microfoni. Converte il suono in un segnale di tensione variabile che viene ricevuto da Arduino per controllare l'accensione e lo spegnimento del LED.

**2. Principio di Funzionamento**

![](media/B14.png)

Quando viene rilevato un suono, la pellicola elettretica nel microfono vibra, modificando la capacità e generando una sottile variazione di tensione.

Successivamente, utilizziamo il chip LM3 per costruire un circuito adeguato che amplifica il suono rilevato, regolabile tramite un potenziometro. Ruotandolo in senso orario si aumenta il guadagno.

**3. Schema di Collegamento**

![](media/B15.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.1：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33; //Define sound as IO33

void setup()
{
  Serial.begin(9600);
  pinMode(sound,INPUT);
}

void loop()
{
  int value = analogRead(sound);
  Serial.println(value);
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale impostando la velocità a 9600 baud, verrà visualizzato il valore analogico.

![](media/B16.png)

**Regolazione della sensibilità:**

Se si ritiene che la sensibilità del sensore sonoro sia adeguata, è possibile regolare il potenziometro del sensore (a destra per la massima sensibilità, a sinistra per la minima sensibilità).

![](media/B17.png)

**6. Approfondimento**

La luce da corridoio comunemente vista è un tipo di luce controllata dal suono. Nel frattempo, include anche una fotoresistenza. Diversamente da questa, qui costruiamo un modello in cui un LED è influenzato solo dal suono. Quando il volume analogico supera 100, il LED si accende per 2 secondi e poi si spegne.

- **Diagramma di Flusso:**

![](media/B18.png)

- **Schema di Collegamento:**

![](media/B19.png)

- **Codice:**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.2：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33;   //Define sound to IO33
int led = 25;      //Define led to IO25

void setup()
{
  pinMode(led,OUTPUT);   //Set IO25 to output 
}

void loop()
{
  int value = analogRead(sound);    //Read analog value of IO33 and assign it to value
  if(value > 100)
  {                  //Judge whether value is greater than 100
    digitalWrite(led,HIGH);         //If IO25 pin outputs high level, LED lights up
    delay(2000);
  }
  else
  {
    digitalWrite(led,LOW);          //If IO25 pin outputs low level, LED lights off
  }
}
```

- **Risultato del Test**

Quando il valore rilevato dal sensore sonoro è superiore a 100, il LED rosso si accende.