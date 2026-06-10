### Proyecto 1 Parpadeo de LED

**1. Descripción**

El parpadeo de LED es un proyecto sencillo diseñado para principiantes. Solo necesitas instalar un LED en la placa Arduino y cargar el código en el IDE de Arduino. Este proyecto refuerza el aprendizaje del marco conceptual de Arduino y el uso de métodos para principiantes.

**2. Principio de Funcionamiento**

![](media/A16.png)

- **LED:** El diagrama de circuito anterior corresponde al LED. En términos generales, los puertos IO limitados en corriente de salida pueden causar un brillo bajo del LED, por lo que se utiliza un transistor NPN (Q2) en el circuito como interruptor. En este caso, el LED se encenderá si la base (pin 1) del transistor está en un nivel alto. Por el contrario, el LED se apaga cuando la base está en bajo.

- **Interruptor de transistor:** Para entender claramente su principio, se requiere cierto conocimiento de circuitos electrónicos. Para más detalles, consulte materiales por su cuenta. En resumen, el encendido y apagado del LED depende de los niveles alto y bajo de la base del transistor, que son determinados por el pin en la placa de desarrollo. El LED se enciende cuando la base (pin 1) está en nivel alto, y se apaga cuando la base está en bajo.

**3. Diagrama de Conexiones：**

![](media/A17.png)

**4. Cargar Código**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 1: LED Blinking
  http://www.keyestudio.com
*/
int ledPin = 5; //Define LED to connect with pin IO5
void setup() 
{
  pinMode(ledPin, OUTPUT);//Set the mode to output
}

void loop() 
{
  digitalWrite(ledPin, HIGH); //Output a high level, LED lights up
  delay(1000);//Delay 1000ms 
  digitalWrite(ledPin, LOW); //Output a low level, LED goes off
  delay(1000);
}
```

**5. Resultado de la Prueba**

Después de cargar el código y encender la alimentación, el LED se encenderá durante 1 s y se apagará durante 1 s.