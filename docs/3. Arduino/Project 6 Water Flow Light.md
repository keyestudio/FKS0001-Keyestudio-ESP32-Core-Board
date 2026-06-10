### Progetto 6 Luce a Flusso d'Acqua

**1. Descrizione**

Questo semplice progetto di luce a flusso d'acqua ti aiuta a imparare il confezionamento elettronico. In questo progetto, controlleremo i LED per cambiare colore a una velocità specificata tramite una scheda Arduino.

**2. Schema di Collegamento**

![](media/A25.png)

**3. Codice di Test**

Una luce a flusso d'acqua significa che i LED si accendono da sinistra a destra e poi da destra a sinistra.  
In questo esperimento, usiamo pin continui, così che l'istruzione "for" possa essere utilizzata non solo per impostare la modalità output (sostituendo i pin con una variabile ciclica nel codice) ma anche per l'output.

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 6 Water Flow Light
  http://www.keyestudio.com
*/
void setup() 
{
  for(int i = 12;i <= 15 ;i++) //Use "for" loop statement to set IO12-IO15 pin to output mode
  {  
    pinMode(i,OUTPUT);
  }
}

void loop() 
{
  for(int i = 12; i <= 15; i++)//Use "for" loop statement to light up LED on IO12-IO15 pin in sequence 
  {		
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
  for(int i = 15; i >= 12; i--)//Use "for" loop statement to light up LED on IO15-IO12 pin in sequence 
  {		  
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
}
```

**4. Risultato del Test**

Dopo aver caricato il codice e acceso l'alimentazione, i LED si accendono da sinistra a destra e poi da destra a sinistra