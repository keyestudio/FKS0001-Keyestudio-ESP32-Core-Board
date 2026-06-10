### Proyecto 29 Control Remoto IR

**1. Descripción**

El control remoto IR utiliza señal IR para controlar el LED, lo que simplifica en gran medida el proceso de control del LED.

**2. Principio de Funcionamiento**

![](media/B41.png)

En este proyecto, a menudo usamos un portador de aproximadamente 38K para la modulación.

El sistema de control remoto IR incluye modulación, emisión y recepción. Envía datos mediante modulación, lo que mejora la eficiencia de transmisión y reduce el consumo de energía.

Generalmente, la frecuencia de modulación del portador está dentro de 30kHz~60kHz (usualmente 38kHz). El ciclo de trabajo de la onda cuadrada es 1/3, como se muestra a continuación, lo cual está determinado por el oscilador de cristal de 455kHz en el extremo emisor.

Una división entera de frecuencia es esencial para el oscilador de cristal en este extremo, y el coeficiente de frecuencia usualmente evalúa 12. Por lo tanto, 455kHz÷12≈37.9kHz≈38kHz.

**Diagrama completo de emisión del portador de 38KH:**

![](media/B42.jpg)

**Frecuencia del portador:** 38KHz

**Longitud de onda:** 940nm

**Ángulo de recepción:** 90°

**Distancia de control:** 6M

**Diagrama esquemático de los botones del control remoto:**

![](media/B43.png)

**3. Diagrama de Conexiones**

![](media/B44.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 29.1 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

const uint16_t recvPin = 19;  // Infrared receiving pin
IRrecv irrecv(recvPin);  // Create a class object used to receive class
decode_results results;   // Create a decoding results class object
long ir_rec;

void setup()
{
  Serial.begin(9600); // Initialize the serial port and set the baud rate to 9600
  irrecv.enableIRIn(); // start receiving signals
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value; //assign the signal to the variable ir_rec
    if(ir_rec != 0)
    {		//Prevente the code from repeating execute when the button is pressed 
        Serial.print(ir_rec, HEX); //Print the variable ir_rec in hexadecimal
        Serial.println();//Wrapping lines
    }
    irrecv.resume(); //Release the IR remote and receive the next value.
  }
} 
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial y configure la velocidad en 9600.

Presione el botón en el control remoto y verá el valor en hexadecimal.

![](media/B45.png)

**6. Ampliación de Conocimientos**

A continuación, usaremos un control remoto IR para controlar el LED. Presione OK para encender el LED y presione nuevamente para apagarlo.

**Diagrama de Conexiones：**

![](media/B46.png)

**Código：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 29.2 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

int led = 25;
int led_val = 0;
const uint16_t recvPin = 19;  // Infrared receiving pin
IRrecv irrecv(recvPin);       // Create a class object used to receive class
decode_results results;       // Create a decoding results class object
long ir_rec;

void setup() 
{
  Serial.begin(9600);   // Initialize the serial port and set the baud rate to 9600
  irrecv.enableIRIn();  // start receiving signals
  pinMode(led, OUTPUT);
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value;      //assign the signal to the variable ir_rec
    if (ir_rec != 0) 
    {           //Prevente the code from repeating execute when the button is pressed
      if (ir_rec == 0xFF02FD) //Determine whether the received IR signal is from button OK
      {  
        led_val = !led_val;      //Reverse a variable. If the initial value is 0, it turns to 1 after reversing  
        digitalWrite(led, led_val);
      }
    }
    irrecv.resume();  //Release the IR remote and receive the next value.
  }
}
```

**Resultado de la Prueba:** 

Presione OK para encender el LED y presione nuevamente para apagarlo.