### Progetto 17 Allarme di Invasione

**1. Descrizione**

Questo sistema di allarme di invasione è in grado di rilevare intrusi in case o piccoli uffici e avvisare il proprietario per prendere misure tempestive.

In questo progetto, il sensore monitora una determinata area. Un dispositivo sulla scheda Arduino attiverà il LED per accendersi e il buzzer per emettere un segnale acustico di avviso se viene rilevato un movimento in quella zona.

Virtualmente, questo modulo presenta praticità, facile installazione e costi contenuti. Oltre che per abitazioni e uffici, si applica anche a fabbriche, magazzini e mercati, proteggendo in larga misura la sicurezza della proprietà.

**2. Principio di Funzionamento**

![](media/A64.png)

Il corpo umano (37°C) emette sempre raggi infrarossi con una lunghezza d’onda di 10μm, che si avvicina a quella rilevata dal sensore.

Per questo motivo, questo modulo è in grado di rilevare il movimento di esseri umani. Se presente, il sensore PIR emette un segnale alto per circa 3 secondi. In assenza di movimento, emette un segnale basso.

**3. Schema di Collegamento**

![](media/A65.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.1 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;    //Define IO5 as PIR sensor pin 

void setup() 
{
  pinMode(pir,INPUT);   //Set IO5 pin to input 
  Serial.begin(9600);
}

void loop() 
{
  int pir_val = digitalRead(pir); 	//Read the PIR result and assign it to pir_val 
    Serial.print("pir_val:"); //Print “pir_val”
	Serial.println(pir_val);
    delay(500);
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale impostando la velocità a 9600 baud; la porta seriale mostrerà il valore del PIR. Se il sensore PIR rileva una persona, verrà visualizzato 1.

![](media/A66.png)

**6. Espansione della Conoscenza**

Realizziamo un allarme di invasione. Quando il sensore PIR rileva un essere umano, il LED si accende e il buzzer emette un suono. Al contrario, il LED si spegne e il buzzer resta silenzioso.

- **Diagramma di Flusso：**

![](media/A67.png)

- **Schema di Collegamento：**

![](media/A68.png)

- **Codice：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.2 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;		//Set PIR sensor pin to IO5
int red_led = 18;	//Set red LED to pin IO18
int buzz = 19;		//Set buzzer to pin IO19

void setup() 
{
  // put your setup code here, to run once:
  pinMode(pir,INPUT);		//Set PIR pin to input mode 
  pinMode(red_led,OUTPUT);	//Set LED pin to output mode  
  pinMode(buzz,OUTPUT);		//Set buzzer pin to output mode 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int pir_val = digitalRead(pir);
  if(pir_val == 1)
  {
    digitalWrite(red_led,HIGH);
    digitalWrite(buzz,HIGH);
  }
  else
  {
    digitalWrite(red_led,LOW);
    digitalWrite(buzz,LOW);
  }
}
```

**Risultato del Test**

Se il sensore PIR rileva una persona nelle vicinanze, il LED rosso si accenderà e il buzzer suonerà.