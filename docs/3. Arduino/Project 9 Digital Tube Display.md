### Proyecto 9 Pantalla de Tubo Digital

**1. Descripción**

Esta pantalla de tubo de 4 dígitos es un dispositivo utilizado para mostrar conteos o tiempo, capaz de mostrar números del 0 al 9 y letras simples. Está compuesta por cuatro tubos digitales, cada uno con siete diodos emisores de luz (LED).

Además, se pueden realizar múltiples funciones conectando sus pines a la placa de desarrollo Arduino, como cronometraje y algunos juegos almacenados.

**2. Principio de Funcionamiento**

![](media/A33.png)

TM1650 utiliza el protocolo IIC y adopta dos líneas de bus (SDA y SCL).

**Comando de Datos:** 0x48.  
Este comando indica al TM1650 que encienda los tubos digitales en lugar de escanear teclas.

**Comando de Visualización:**

![](media/A34.png)

En realidad, es un byte de datos con diferentes bits que representan distintas funciones.  
**bit[6:4]:** Ajusta el brillo del LED. Nota que 000 indica el brillo máximo.  
**bit[3]:** Determina si hay un punto decimal.  
**bit[0]:** Determina si se enciende la pantalla.

**Encendido del Tubo Digital**  
Ejemplo: Brillo nivel 8 sin punto decimal significa 0x05.  
Pasos: Señal de inicio — Enviar 0x48 — Dispositivo esclavo recibe — Enviar 0x05 — Dispositivo esclavo recibe — Señal de fin  
Después de encender, no es necesario enviar repetidamente 0x48, ya que la función del tubo digital ha sido confirmada.  
Además, el brillo y los métodos de visualización pueden enumerarse con múltiples datos en un solo lugar, lo que resulta claro y ahorra espacio.

**Apagado del Tubo Digital**  
Pasos: Señal de inicio — Enviar 0x48 — Dispositivo esclavo recibe — Enviar 0x00 — Dispositivo esclavo recibe — Señal de fin

**Visualización de Números en el Tubo Digital**  
Primero indicamos al TM1650 que muestre números en el tubo predeterminado. Luego, el número se mostrará. Sus ocho bits corresponden a ocho segmentos, con 1 para encender y 0 para apagar. Si hay dudas sobre la relación correspondiente, puede encenderse bit a bit en un ciclo.

Por ejemplo, cuando el bit 1 está encendido y muestra un 8, el dato es 0x68. Si hay un punto decimal, el 8 también se mostrará al enviar 0x7f.  
Pasos: Señal de inicio — Enviar 0x68 — Dispositivo esclavo recibe — Enviar 0x7f — Dispositivo esclavo recibe — Señal de fin  
Resultado: 8 se muestra en el bit 1.

Para mayor comodidad, se puede crear un arreglo con los valores correspondientes del 0 al 9. Tras mejoras adicionales, es posible mostrar números, ajustar brillo, desplazar el punto decimal y los tubos.

**3. Diagrama de Conexiones**

![](media/A35.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.1 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
    DigitalTube.displayFloatNum(9999);   //Values or variables added to the parentheses can be displayed through the digital tube 
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, la pantalla de tubo digital muestra "9999", como se muestra a continuación.

![](media/A36.png)

**6. Código Extendido**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.2 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  for(int num=0; num<10000; num++)
  {   //Si num es menor que 10000, num aumentará en 1 en cada ciclo
    DigitalTube.displayFloatNum(num);   //Valores o variables en los paréntesis pueden mostrarse a través del tubo digital
    delay(100);
  }
}
```

**7. Resultado de la Prueba**

Después de subir el código, el tubo digital muestra del 1 al 9999 mediante un ciclo "for".