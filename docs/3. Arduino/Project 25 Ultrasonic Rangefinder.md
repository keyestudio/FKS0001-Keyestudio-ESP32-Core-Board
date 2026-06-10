### Proyecto 25 Medidor de Distancia Ultrasónico

**1. Descripción**

Este medidor de distancia ultrasónico mide la distancia de obstáculos emitiendo ondas sonoras y luego recibiendo el eco. Es decir, la distancia no es un valor inmediato, sino uno observado mediante un cálculo teórico de la diferencia de tiempo entre el emisor y el receptor.

El ultrasónico es capaz de detectar la forma de objetos, configurar puertas automáticas y estimar la velocidad de flujo y presión.

Además, soporta trabajos cooperativos con computadoras. Como resultado, el valor medido puede ser transmitido a computadoras a través de la placa Arduino.

En la vida diaria, se utiliza ampliamente para motores, servos y LEDs, así como en sistemas (navegación automática, control y sistemas de monitoreo de seguridad).

**2. Principio de Funcionamiento**

![](media/B29.png)

Como todos sabemos, el ultrasónico es un tipo de señal de onda sonora inaudible con alta frecuencia. Similar a un murciélago, este módulo mide la distancia de obstáculos calculando la diferencia de tiempo entre la emisión de la onda y la recepción del eco.

**Distancia máxima:** 3M

**Distancia mínima:** 5cm

**Ángulo de detección:** ≤15°

**3. Diagrama de Conexiones**

![](media/B30.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 25.1：Ultrasonic Rangefinder
  http://www.keyestudio.com
*/
int distance = 0; //Define una variable para recibir el valor de distancia 
int EchoPin = 14; //Conecta el pin Echo a io14
int TrigPin = 13; //Conecta el pin Trig a io13

float checkdistance() { //Adquiere la distancia 
  // conserva un nivel bajo corto para asegurar un pulso alto claro:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);    //Retraso de 2us
  //Dispara el sensor con un pulso alto de 10us o más 
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);		//Retraso de 10us
  digitalWrite(TrigPin, LOW);
  //Lee la señal del sensor: un pulso de nivel alto
  //La duración se detecta desde el momento de enviar el comando "ping" hasta recibir la señal de eco (unidad: us).
  float distance = pulseIn(EchoPin, HIGH) / 58.00;  //Convierte a distancia
  delay(10);
  return distance; //Devuelve el valor de distancia
}

void setup() 
{
  Serial.begin(9600);//Configura la velocidad en baudios a 9600
  pinMode(TrigPin, OUTPUT);//Configura el pin Trig como salida
  pinMode(EchoPin, INPUT);  //Configura el pin Echo como entrada 
}

void loop() 
{
  distance = checkdistance();   //Asigna el valor leído a "distance" 
  if (distance < 4 || distance >= 400) //Muestra "-1" si excede el rango de detección 
  {  
    distance = -1;
  }
  Serial.print("ditance: ");
  Serial.print(distance);
  Serial.println(" CM");
  delay(200);
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura la velocidad en baudios a 9600, el puerto serial imprimirá el valor de la distancia.

![](media/B31.png)

**6. Ampliación de Conocimientos**

Vamos a hacer un medidor de distancia.

Mostramos caracteres en un LCD 1602. Programa para mostrar "Keyestudio" en (3,0) y “distance:” en (0,1) seguido del valor de distancia en (9,1).

Cuando el valor es menor que 100 (o 10), aún queda un residuo del tercer (o segundo) dígito. Por lo tanto, es necesario un juicio "if" para determinar una condición específica.

**Diagrama de Conexiones：**

![](media/B32.png)

**Código：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 25.2：Ultrasonic Rangefinder
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); //configura la dirección del LCD a 0x27 para una pantalla de 16 caracteres y 2 líneas

int distance = 0; //Define una variable para recibir el valor de distancia 
int EchoPin = 14; //Conecta el pin Echo a io14
int TrigPin = 13; //Conecta el pin Trig a io13
float checkdistance() { //Adquiere la distancia 
  // conserva un nivel bajo corto para asegurar un pulso alto claro:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);
  //Dispara el sensor con un pulso alto de 10us o más 
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(TrigPin, LOW);
  // Lee la señal del sensor: un pulso de nivel alto
  //La duración se detecta desde el momento de enviar el comando "ping" hasta recibir la señal de eco (unidad: us).
  float distance = pulseIn(EchoPin, HIGH) / 58.00;  //Convierte a distancia
  delay(10);
  return distance;
}

void setup() 
{
  	Serial.begin(9600);//Configura la velocidad en baudios a 9600
  	pinMode(TrigPin, OUTPUT);//Configura el pin Trig como salida
  	pinMode(EchoPin, INPUT);  //Configura el pin Echo como entrada 
    lcd.init(); // inicializa el lcd
    // Imprime un mensaje en el LCD.
    lcd.backlight();
    lcd.setCursor(3,0);
    lcd.print("Keyestudio");
}

void loop() 
{
  distance = checkdistance();
 
  if (distance < 2 || distance >= 400) //Muestra "-1" si excede el rango de detección 
  {  
    distance = -1;
  }
  if(distance < 100 && distance > 10){             //Elimina la sombra del tercer dígito cuando el valor baja a dos dígitos
    lcd.setCursor(11,1);
    lcd.print(" ");
  }
  if(distance < 10)//Elimina las sombras de dos dígitos cuando el valor baja a un dígito
  {              
    lcd.setCursor(10,1);
    lcd.print(" ");
  }
  lcd.setCursor(0,1);
  lcd.print("distance:");
  lcd.setCursor(9,1);
  lcd.print(distance);
  delay(200);
}