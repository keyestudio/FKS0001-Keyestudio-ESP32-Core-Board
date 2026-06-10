### Projekt 14 Zähler

**1. Beschreibung**

Der Arduino 4-Bit Digitalröhrenzähler kann Zahlen im Bereich von 0 bis 9999 erfassen. Er verfügt über eine Anzeige-Geschwindigkeit, Zählmodus-Anpassung sowie eine Rücksetzfunktion. Dieses Modul wird häufig in Echtzeit-Zählern (wie Tasterbetätigung und DC-Motor-Drehzahlerfassung), Spiel- und Versuchsausrüstung eingesetzt.

**2. Flussdiagramm**

![](media/A58.png)

**3. Schaltplan**

![](media/A59.png)

**4. Testcode**

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

**4. Testergebnis**

Nach dem Anschließen der Verkabelung und Hochladen des Codes drücken Sie die grüne Taste, um 1 zu addieren, die gelbe Taste, um 1 zu subtrahieren, und die rote Taste, um zurückzusetzen. Halten Sie die Taste gedrückt, wird der angezeigte Wert kontinuierlich erhöht oder verringert.