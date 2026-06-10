### Progetto 12 Servo

**1. Descrizione**

Questo servo offre alte prestazioni e alta precisione con un angolo massimo di rotazione di 180°. Pesando solo 9g, è perfettamente adatto a qualsiasi dispositivo mini in molteplici occasioni. Inoltre, presenta un tempo di avvio breve, basso rumore e forte stabilità.

**2. Principio di Funzionamento**

**Intervallo angolare:** 180° (360°, 180° e 90°)

**Tensione di alimentazione:** 3.3V o 5V

**Pin:** Tre fili

![](media/A49.png)

**GND:** Messa a terra (marrone)

**VCC:** Un pin rosso che si collega a un'alimentazione +5V (3.3V)

**S:** Un pin di segnale arancione controllato tramite segnale PWM

![](media/A50.png)

**Principio di Controllo**: L'angolo di rotazione è controllato tramite il duty cycle del PWM. Teoricamente, il ciclo standard del PWM è 20ms (50Hz), quindi la larghezza dell'impulso dovrebbe variare tra 1ms e 2ms. Tuttavia, la larghezza reale dell'impulso raggiunge 0.5ms~2.5ms, corrispondente a 0°～180°. Si noti che, per lo stesso segnale, l'angolo di rotazione può variare a seconda della marca del servo.

**3. Schema di Collegamento**

![](media/A51.png)

Aggiungere una fonte di alimentazione esterna invece di usare solo l'USB per l'alimentazione.

![](media/A52.png)

**4. Codice di Test**

```
int servoPin = 4;//servo PIN

void setup() 
{
  pinMode(servoPin, OUTPUT);//servo pin is set to output
}

void loop() 
{
  for(int i = 0 ; i <= 180 ; i++) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 0° to 180°
  delay(10);//delay 10ms
  }
  for(int i = 180 ; i >= 0 ; i--) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 180° to 0°
  delay(10);//delay 10ms
  }
}

void servopulse(int pin, int myangle) 
{ //Impulse function
  int pulsewidth = map(myangle, 0, 180, 500, 2500); //Map Angle to pulse width
  for (int i = 0; i < 10; i++) 
  { //Output a few more pulses
    digitalWrite(pin, HIGH);//Set the servo interface level to high
    delayMicroseconds(pulsewidth);//The number of microseconds of delayed pulse width value
    digitalWrite(pin, LOW);//Lower the level of servo interface
  }
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, il servo inizia a ruotare da 0° a 180° e poi in senso inverso.