### Proyecto 6 Luz de Flujo de Agua

**1. Descripción**

Este sencillo proyecto de luz de flujo de agua te ayuda a aprender sobre el empaquetado electrónico. En este proyecto, controlaremos LEDs para cambiar el color a una velocidad especificada mediante una placa Arduino.

**2. Diagrama de Conexiones**

![](media/A25.png)

**3. Código de Prueba**

Una luz de flujo de agua significa que las luces LED se encienden de izquierda a derecha y luego de derecha a izquierda.  
En este experimento, usamos pines continuos, de modo que la instrucción "for" puede utilizarse no solo para configurar el modo de salida (reemplazando los pines con una variable circular en el código) sino también para la salida.

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

**4. Resultado de la Prueba**

Después de subir el código y encender la alimentación, los LEDs se encienden de izquierda a derecha y luego de derecha a izquierda.