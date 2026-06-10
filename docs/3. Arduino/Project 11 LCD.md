### Proyecto 11 LCD

**1. Descripción**

El Arduino I2C 1602 LCD es un dispositivo auxiliar comúnmente utilizado para placas de desarrollo MCU para conectar con sensores y módulos externos. Cuenta con una pantalla LCD de 16 caracteres de ancho y 2 líneas, con brillo ajustable. Este módulo programable es conveniente para la edición, visualización y gestión de datos. Además, puede mostrar no solo caracteres y cifras, sino también valores de sensores, como temperatura, humedad o presión.

Como resultado de su utilidad, la pantalla se aplica ampliamente en muchos campos, incluyendo productos para hogares inteligentes, sistemas de monitoreo industrial, sistemas de control de robots y sistemas electrónicos automotrices.

**2. Principio de Funcionamiento**

![](media/A44.png)

Es el mismo principio de comunicación IIC. Las funciones subyacentes han sido empaquetadas en librerías para que puedas llamarlas directamente. Si estás interesado en ellas, puedes profundizar en los principios de conducción subyacentes.

**3. Diagrama de Conexiones**

![](media/A45.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 11 LCD
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); // set the LCD address to 0x27 for a 16 chars and 2 line display

void setup()
{
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();		//Turn on the LCD backlight 
    lcd.setCursor(2,0);		//Set the display position 
    lcd.print("Hello,world!");		//LCD displays "Hello, world!"
    lcd.setCursor(2,1);	
    lcd.print("keyestudio!");		//LCD displays "keyestudio!"
}

void loop()
{
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, enciende el LCD, se mostrarán "Hello, world!" y "keyestudio!" en la pantalla LCD.

![](media/A46.png)

Si los caracteres no se ven claros, ajusta el potenciómetro de la luz de fondo con un destornillador pequeño de ranura (Por favor usa la fuerza adecuada para ajustar). Conecta una fuente de alimentación externa si es necesario.

![](media/A47.png)

![](media/A48.png)