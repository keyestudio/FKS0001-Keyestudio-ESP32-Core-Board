### Proyecto 7 Zumbador Activo

**1. Descripción**

Un zumbador activo es un componente utilizado como alarma, recordatorio o dispositivo de entretenimiento, que ofrece un sonido confiable. Además, permite estimular sonidos altamente controlables, haciendo nuestros proyectos más interesantes.

**2. Principio de Funcionamiento**

![](media/A26.png)

Un zumbador activo integra un multivibrador, por lo que emite sonido solo mediante voltaje DC. El pin 1 del zumbador se conecta a VCC y el pin 2 es controlado por un tríodo. Cuando se proporciona un nivel alto a la base (pin 1) del tríodo, su colector (pin 3) y emisor (pin 2) se conectan a GND, y entonces el zumbador emite sonido.

Por el contrario, si se ofrece un nivel bajo a la base, el resto de los pines quedarán desconectados, por lo que el zumbador permanecerá en silencio.

**3. Diagrama de Conexiones**

![](media/A27.png)

**4. Código de Prueba**

```
 /*
  keyestudio ESP32 Inventor Learning Kit
  Project 7 Active Buzzer
  http://www.keyestudio.com
*/
int buzzer = 5; //Define buzzer connected to IO5 pin 

void setup() 
{
  pinMode(buzzer, OUTPUT);//Set the output mode 
}

void loop() 
{
  digitalWrite(buzzer, HIGH); //IO5 pin outputs a high level to cause the buzzer to emit sound 
  delay(1000);					//Delay 1000ms
  digitalWrite(buzzer, LOW); //IO5 outputs a low level to prevent the buzzer to emit sound 
  delay(1000);
}
```

**5. Resultado de la Prueba**

Después de subir el código y encender, el zumbador emite sonido durante 1s y permanece en silencio durante 1s.