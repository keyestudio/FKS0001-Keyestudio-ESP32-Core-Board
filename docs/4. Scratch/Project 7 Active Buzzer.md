### Proyecto 7 Zumbador Activo

**1. Descripción**

Un zumbador activo es un componente utilizado como alarma, recordatorio o dispositivo de entretenimiento, que ofrece un sonido confiable.

Además, permite estimular sonidos altamente controlables, haciendo nuestros proyectos más interesantes.

**2. Principio de Funcionamiento**

![](media/A82.png)

Un zumbador activo integra un multivibrador, por lo que emite sonido solo mediante voltaje DC. El pin 1 del zumbador se conecta a VCC y el pin 2 es controlado por un tríodo. Cuando se proporciona un nivel alto a la base (pin 1) del tríodo, su colector (pin 3) y emisor (pin 2) se conectan a GND, y entonces el zumbador emite sonido.

Por el contrario, si se ofrece un nivel bajo a la base, el resto de los pines quedarán desconectados, por lo que el zumbador permanecerá en silencio.

**3. Diagrama de Conexiones**

![](media/A83.png)

**4. Código de Prueba**

Si la placa de desarrollo emite un nivel alto, el zumbador emitirá sonido. Si emite un nivel bajo, el zumbador dejará de sonar.

1. Arrastra los dos bloques básicos de código.

![](media/A84.png)

2. Arrastra los siguientes bloques de la sección "Buzzer" y configura el pin IO5 en HIGH. Luego establece el tiempo de retardo en 1s.

![](media/A85.png)

3. Arrastra los siguientes bloques de la sección "Buzzer" y configura el pin IO5 en LOW. Luego establece el tiempo de retardo en 1s.

![](media/A86.png)

**Código Completo：**

![](media/A87.png)

**5. Resultado de la Prueba**

Después de subir el código y encender la alimentación, el zumbador emite sonido durante 1s y permanece en silencio durante 1s.

**6. Explicación del Código**

Bloque de salida para el zumbador. Primero definimos el pin como IO5 y luego configuramos la salida en "HIGH" o "LOW". El zumbador emitirá un pitido cuando esté en HIGH, mientras que permanecerá en silencio en LOW.

![](media/A88.png)