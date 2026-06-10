### Progetto 2 LED Respirante

**1. Descrizione**

Il LED respirante Arduino utilizza il PWM programmabile a bordo per generare un'onda analogica. Dopo l'accensione, la luminosità del LED può essere regolata tramite il duty cycle dell'onda per realizzare l'effetto di LED respirante.

In questo modo, la luce ambientale può essere simulata variando la luminosità del LED nel tempo. Inoltre, il LED respirante può formare una mini luce colorata per creare un ambiente tranquillo e caldo.

**2. Cos'è il PWM?**

Il PWM controlla l'uscita analogica tramite mezzi digitali, permettendo di regolare il duty cycle dell'onda (un segnale che alterna ciclicamente tra livello alto e livello basso).

Per Arduino, le porte digitali di uscita di tensione sono LOW e HIGH, che corrispondono rispettivamente a 0V e 5V. Generalmente, definiamo LOW come 0 e HIGH come 1. Arduino emette 500 segnali di 0 o 1 in 1 secondo. Se sono "1", verranno emessi 5V. Al contrario, se sono tutti 0, l'uscita sarà 0V. Oppure, se sono 010101010101..., la media dell'uscita sarà 2,5V.

In altre parole, il rapporto di uscita tra 0 e 1 influenza il valore di tensione; più segnali 0 e 1 vengono emessi per unità di tempo, più preciso sarà il controllo.

I GPIO34, 35, 36 e 39 dell'ESP32 non possono utilizzare il PWM.

![](media/A18.png)

**3. Schema di Collegamento**

![](media/A19.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. Risultato del Test**

Dopo aver caricato il codice, vedremo il LED illuminarsi e spegnersi lentamente, proprio come il ritmo della respirazione.