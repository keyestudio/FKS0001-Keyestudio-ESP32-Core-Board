### Proyecto 28 Puerta Inteligente

**1. Descripción**

La puerta inteligente es un sistema de estacionamiento inteligente que integra MCU y sensor ultrasónico, el cual controla automáticamente la puerta según la distancia de los vehículos, para así controlar mejor el acceso de los autos.

Cuando se alcanza cierta distancia, la MCU recibe la señal del sensor y estima la distancia mediante la intensidad de la señal. Si el auto se está acercando o alejando, la MCU abrirá o cerrará la puerta mediante un servo.

**2. Diagrama de Flujo**

![](media/B39.png)

**3. Diagrama de Conexiones**

![](media/B40.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 28 Intelligent Gate
  http://www.keyestudio.com
*/
#define servo_pin  25
int distance = 0; //Define una variable para recibir la distancia
int EchoPin = 14; //Conectar pin Echo a IO14
int TrigPin = 13; //Conectar pin Trig a IO13

//Programa de medición ultrasónica
float checkdistance() { //Adquirir distancia
  //mantener un nivel bajo corto para asegurar un pulso alto claro:
  digitalWrite(TrigPin, LOW);
  delayMicroseconds(2);
  //Disparar el sensor con un pulso alto de 10us o más
  digitalWrite(TrigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(TrigPin, LOW);
  //Leer la señal del sensor: un pulso de nivel alto
  //La duración se detecta desde el envío del comando "ping" hasta la recepción del eco (unidad: us).
  float distance = pulseIn(EchoPin, HIGH) / 58.00;  //Convertir a distancia
  delay(10);
  return distance;
}

//Programa de rotación del servo
void Set_Angle(int angle_val) //Función de impulso
{ 
  int pulsewidth = map(angle_val, 0, 180, 500, 2500); //Mapear ángulo a ancho de pulso
  for (int i = 0; i < 10; i++) { //Emitir algunos pulsos más
    digitalWrite(servo_pin, HIGH);//Poner el nivel del pin del servo en alto
    delayMicroseconds(pulsewidth);//Número de microsegundos del ancho de pulso
    digitalWrite(servo_pin, LOW);//Bajar el nivel del pin del servo
    delay(20 - pulsewidth / 1000);  //Agregar el paréntesis
  }
} 

void setup() 
{
  // coloca tu código de configuración aquí, para que se ejecute una vez:
  pinMode(servo_pin,OUTPUT);
  pinMode(TrigPin, OUTPUT);//Configurar pin Trig como salida
  pinMode(EchoPin, INPUT);  //Configurar pin Echo como entrada
}

void loop() 
{
  // coloca tu código principal aquí, para que se ejecute repetidamente:
 distance = checkdistance();
 Serial.println();
  if(distance < 30)
  {
    Set_Angle(180);
    delay(5000);//Esperar 5s   
  }
  if(distance > 30)
  {
    Set_Angle(0);
  }
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, el servo girará a 180° durante 5s si la distancia detectada es menor a 30cm. Por el contrario, el servo girará a 0°.