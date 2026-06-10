### Proyecto 10 Pantalla de Matriz de Puntos

**1. Descripción**

Este módulo consiste en una matriz de puntos LED de 8x8 con un pin de control para cada fila y cada columna para ajustar el brillo del LED. Al conectarlo con la placa Arduino, el brillo del LED se controla para mostrar caracteres y figuras mediante programación en Arduino. De esta manera, se pueden mostrar caracteres simples, números y figuras. También puede aplicarse en máquinas de juego o pantallas.

**2. Principio de Funcionamiento**

![](media/A37.png)

MAX7219 es un IC con comunicación SPI y puede usarse para controlar la matriz de puntos 8x8. La comunicación SPI del MAX7219 está integrada en nuestras librerías y puedes llamarla directamente.

**Operación del Módulo Matriz de Puntos**

Haz clic en el enlace para el Módulo: [http://dotmatrixtool.com/#](http://dotmatrixtool.com/#)

**Pasos:**

1. Haz clic en el enlace y configura la altura y el ancho de la matriz de puntos. Aquí configuramos ambos a 8.

![](media/A38.png)

2. Configura "Byte Order" a "Column Major".

![](media/A39.png)

3. Configura "Endian" a "Big Endian".

![](media/A40.png)

4. Haz clic en los cuadros blancos para formar el patrón que deseas (haz clic de nuevo para deseleccionar), y luego haz clic en "Generate" para generar un arreglo para este ícono. Copia este arreglo y pégalo en el código, y entonces el patrón se mostrará en la matriz de puntos.

![](media/A41.png)

**3. Diagrama de Conexiones**

![](media/A42.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 10 Dot Matrix Display
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x30, 0x78, 0x7c, 0x3e, 0x3e, 0x7c, 0x78, 0x30};

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);  
}

void loop()
{
  for(int i=0; i < 8; i++)
  {
      lc.setRow(0,i,IMAGES[i]);
  }
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, un corazón se mostrará en la matriz de puntos, como se muestra a continuación.

![](media/A43.png)