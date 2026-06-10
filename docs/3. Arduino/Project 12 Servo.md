### Proyecto 12 Servo

**1. Descripción**

Este servo cuenta con alto rendimiento y alta precisión con un ángulo máximo de rotación de 180°. Con un peso de solo 9g, es perfectamente adecuado para cualquier dispositivo mini en múltiples ocasiones. Además, disfruta de un tiempo de arranque corto, bajo ruido y gran estabilidad.

**2. Principio de Funcionamiento**

**Rango de ángulo:** 180° (360°, 180° y 90°)

**Voltaje de alimentación:** 3.3V o 5V

**Pin:** Tres cables

![](media/A49.png)

**GND:** Tierra (marrón)

**VCC:** Un pin rojo que se conecta a una fuente de +5V (3.3V)

**S:** Un pin de señal naranja controlado mediante señal PWM

![](media/A50.png)

**Principio de Control**: El ángulo de rotación se controla mediante el ciclo de trabajo del PWM. Teóricamente, el ciclo estándar de PWM es de 20ms (50Hz), por lo que el ancho del pulso debe distribuirse entre 1ms y 2ms. Sin embargo, el ancho real del pulso alcanza de 0.5ms a 2.5ms, lo que corresponde a 0° a 180°. Preste atención a que, para la misma señal, el ángulo de rotación puede variar según la marca del servo.

**3. Diagrama de Conexiones**

![](media/A51.png)

Agregue una fuente de alimentación externa en lugar de usar solo USB para la alimentación.

![](media/A52.png)

**4. Código de Prueba**

```
int servoPin = 4;//servo PIN

void setup() 
{
  pinMode(servoPin, OUTPUT);//servo pin is set to output
}

void loop() 
{
  for(int i = 0 ; i <= 180 ; i++) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 0° to 180°
  delay(10);//delay 10ms
  }
  for(int i = 180 ; i >= 0 ; i--) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 180° to 0°
  delay(10);//delay 10ms
  }
}

void servopulse(int pin, int myangle) 
{ //Impulse function
  int pulsewidth = map(myangle, 0, 180, 500, 2500); //Map Angle to pulse width
  for (int i = 0; i < 10; i++) 
  { //Output a few more pulses
    digitalWrite(pin, HIGH);//Set the servo interface level to high
    delayMicroseconds(pulsewidth);//The number of microseconds of delayed pulse width value
    digitalWrite(pin, LOW);//Lower the level of servo interface
  }
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y cargar el código, el servo comienza a rotar de 0° a 180° y luego en sentido inverso.