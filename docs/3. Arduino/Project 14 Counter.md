### Proyecto 14 Contador

**1. Descripción**

El contador de tubo digital Arduino de 4 bits puede registrar números dentro del rango 0~9999. Cuenta con ajuste de velocidad de visualización, modo de conteo y función de reinicio. Este módulo se aplica ampliamente en contadores en tiempo real (como conteo de pulsaciones de botón y rotación de motor DC), juegos y equipos de experimentación.

**2. Diagrama de flujo**

![](media/A58.png)

**3. Diagrama de conexiones**

![](media/A59.png)

**4. Código de prueba**

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

**4. Resultado de la prueba**

Después de conectar el cableado y subir el código, presione el botón verde para sumar 1, el amarillo para restar 1 y el rojo para reiniciar. Mantenga presionado el botón y el valor mostrado seguirá aumentando o disminuyendo.