### Progetto 14 Contatore

**1. Descrizione**

Il contatore a tubo digitale Arduino a 4 bit può registrare numeri da 0 a 9999. Dispone di regolazione della velocità di visualizzazione, modalità di conteggio e funzione di reset. Questo modulo è ampiamente utilizzato in contatori in tempo reale (come il conteggio delle pressioni di un pulsante e la rotazione di un motore DC), apparecchiature per giochi e sperimentazioni.

**2. Diagramma di flusso**

![](media/A58.png)

**3. Schema di collegamento**

![](media/A59.png)

**4. Codice di test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 14 Counter
  http://www.keyestudio.com
*/
#include "TM1650.h" //Upload TM1650 library file
int item = 0; //Displayed value
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

int res = 17;     //Reset button
int subtract = 18;   //minus button
int  add = 19;       //plus button

void setup(){
    //set the pin connecting with button to input  
  pinMode(res,INPUT);
  pinMode(add,INPUT);
  pinMode(subtract,INPUT);
  for(char b=0;b<4;b++){
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  DigitalTube.displayFloatNum(item);//Digital tube displays item value 
  int red_key = digitalRead(res);            //Red button is the reset button
  int yellow_key = digitalRead(subtract);    //Yellow button is minus 1
  int green_key = digitalRead(add);           //Green button is plus 1
  if(green_key == 0)
  {
    item++;  //operate to add 1, item = item + 1
    delay(200);
  }
  if(yellow_key == 0)
  {
    item--;		//operate to reduce 1, item = item - 1
    delay(200);
  }
  if(red_key == 0)
  {
    item = 0;
    delay(200);
  }
  if (item > 9999)//return to zero when greater than 9999(excessing the display range)
  {  
    item = 0; 
  }
}
```

**4. Risultato del test**

Dopo aver collegato i fili e caricato il codice, premere il pulsante verde per aggiungere 1, il giallo per sottrarre 1 e il rosso per resettare. Tenendo premuto il pulsante, il valore visualizzato continuerà ad aumentare o diminuire.