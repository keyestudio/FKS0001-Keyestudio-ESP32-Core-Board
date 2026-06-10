### Proyecto 20 Pilar de Luz

**1. Descripción**

La resistencia (menos de 1KΩ) de la fotorresistencia varía según la luz, por lo que puede controlar el brillo de la matriz de puntos. Al controlar, conectamos esta resistencia a un pin analógico en la placa para monitorear el cambio de resistencia. De esta manera, la luz controla automáticamente el brillo de la pantalla.

Además, la fotorresistencia se aplica ampliamente en nuestra vida diaria. Por ejemplo, una cortina se abre o cierra automáticamente según la intensidad de la luz exterior.

**2. Principio de Funcionamiento**

![](media/B8.png)

![](media/B9.png)

Cuando está totalmente en oscuridad, la resistencia es igual a 0.2MΩ, y el voltaje en el terminal de señal (punto 2) se acerca a 0V. Cuanto más fuerte es la luz, menor será la resistencia y el voltaje.

**3. Diagrama de Conexiones**

![](media/B10.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.1 Light Pillar
  http://www.keyestudio.com
*/
int light = 34;      //Define light to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(light);	//Read IO34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial y configure la tasa de baudios a 9600, se mostrará el valor analógico, dentro del rango de 0-4095. Cambiar la intensidad de luz alrededor puede modificar su valor.

![](media/B11.png)

**6. Ampliación de Conocimientos**

Usaremos esta fotorresistencia para detectar la intensidad de luz ambiental. Las dos columnas del medio están incluidas en este experimento para representar la intensidad de la luz. Cuanto más fuerte sea, más LEDs se encenderán. Esto forma un "pilar de luz".

- **Diagrama de Conexiones：**

![](media/B12.png)

- **Código：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.2 Light Pillar
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x01,0x03,0x07,0x0F,0x1F,0x3F,0x7F,0xFF}; //Data of light pillar

int light = 34;

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);
  pinMode(light,INPUT);  
}

void loop()
{
  int value = analogRead(light);
  int temp = map(value,0,4095,0,7);  //Convert the range of analog values to 0-7
  lc.setRow(0,3,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 3
  lc.setRow(0,4,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 4
}
```

- **Resultado de la Prueba**

Cuanto más fuerte sea la luz cerca de la fotorresistencia, más alta será la columna de luz en la matriz LED.

![](media/B13.png)