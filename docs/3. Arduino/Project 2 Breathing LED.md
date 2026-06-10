### Proyecto 2 LED Respiratorio

**1. Descripción**

El LED respiratorio de Arduino utiliza PWM programable a bordo para emitir una forma de onda analógica. Después de encender, el brillo del LED puede ajustarse mediante el ciclo de trabajo de la forma de onda para finalmente lograr el efecto de LED respiratorio.

De esta manera, se puede simular la luz ambiental cambiando el brillo del LED con el tiempo. Además, el LED respiratorio puede formar una mini luz colorida para crear un ambiente tranquilo y cálido.

**2. ¿Qué es PWM?**

PWM controla la salida analógica mediante medios digitales, lo que permite ajustar el ciclo de trabajo de la onda (una señal que cambia circularmente entre nivel alto y nivel bajo).

Para Arduino, los puertos digitales de salida de voltaje son LOW y HIGH, que corresponden respectivamente a 0V y 5V. Generalmente, definimos LOW como 0 y HIGH como 1. Arduino emitirá 500 señales de 0 o 1 en 1 segundo. Si son "1", se emitirá 5V. Por el contrario, si son todas 0, la salida será 0V. O si son 010101010101..., el promedio de salida será 2.5V.

En otras palabras, la proporción de salida de 0 y 1 afecta el valor del voltaje; cuanto más señales 0 y 1 se emitan por unidad de tiempo, más preciso será el control.

Los GPIO34, 35, 36 y 39 del ESP32 no pueden usar PWM.

![](media/A18.png)

**3. Diagrama de Conexiones**

![](media/A19.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. Resultado de la Prueba**

Después de cargar el código, veremos que el LED se ilumina y atenúa lentamente, como el ritmo de la respiración.