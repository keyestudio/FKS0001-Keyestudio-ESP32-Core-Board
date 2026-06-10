### Progetto 7 Buzzer Attivo

**1. Descrizione**

Un buzzer attivo è un componente utilizzato come allarme, promemoria o dispositivo di intrattenimento, che produce un suono affidabile. Inoltre, permette di generare suoni altamente controllabili, rendendo i nostri progetti più interessanti.

**2. Principio di Funzionamento**

![](media/A26.png)

Un buzzer attivo integra un multivibratore, quindi emette suono solo tramite tensione DC. Il pin 1 del buzzer è collegato a VCC e il pin 2 è controllato da un triode. Quando viene fornito un livello alto alla base (pin 1) del triode, il suo collettore (pin 3) e l'emettitore (pin 2) si collegano a GND, e il buzzer emette suono.

Al contrario, se forniamo un livello basso alla base, gli altri pin saranno scollegati, quindi il buzzer rimarrà silenzioso.

**3. Schema di Collegamento**

![](media/A27.png)

**4. Codice di Test**

```
 /*
  keyestudio ESP32 Inventor Learning Kit
  Project 7 Active Buzzer
  http://www.keyestudio.com
*/
int buzzer = 5; //Define buzzer connected to IO5 pin 

void setup() 
{
  pinMode(buzzer, OUTPUT);//Set the output mode 
}

void loop() 
{
  digitalWrite(buzzer, HIGH); //IO5 pin outputs a high level to cause the buzzer to emit sound 
  delay(1000);					//Delay 1000ms
  digitalWrite(buzzer, LOW); //IO5 outputs a low level to prevent the buzzer to emit sound 
  delay(1000);
}
```

**5. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, il buzzer emette un suono per 1s e rimane silenzioso per 1s.