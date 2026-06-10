### Proyecto 1 Parpadeo de LED

**1. Descripción**

El parpadeo de LED es un proyecto sencillo diseñado para principiantes. Solo necesitas instalar un LED en la placa Arduino y subir el código en el Arduino IDE. Este proyecto refuerza el aprendizaje del marco conceptual de Arduino y el uso de métodos para principiantes.

**2. Principio de Funcionamiento**

![](media/A7.png)

**LED:** En términos generales, los puertos IO limitados en corriente de salida pueden causar baja luminosidad del LED, por lo que se aplica un transistor NPN (Q2) en el circuito como interruptor. En este caso, el LED se encenderá si la base (pin 1) del transistor está en nivel alto. Por el contrario, el LED se apaga cuando la base está en nivel bajo.

**Interruptor transistor:** En resumen, el LED se enciende cuando la base (pin 1) está en nivel alto. Al mismo tiempo, el colector (pin 3) y el emisor (pin 2) están conectados, y entonces VCC pasa a través de una resistencia limitadora de corriente hacia el LED y finalmente a GND, formando un circuito. Por el contrario, el LED se apaga cuando la base está en nivel bajo. En esta circunstancia, el colector y el emisor están desconectados y el LED se apaga.

**3. Diagrama de Conexiones**

![](media/A8.png)

**4. Código de Prueba**

De acuerdo con los principios anteriores, podemos controlar el LED mediante los niveles de los pines en la placa de desarrollo.

1. Arrastra el siguiente bloque en la sección "Events".

![](media/A9.png)

2. Arrastra el siguiente bloque en la sección "Control".

![](media/A10.png)

3. Arrastra el siguiente bloque en la sección "Pins" y configura el pin IO5 como salida.

   ![](media/A11.png)

4. Arrastra el siguiente bloque en la sección "LED" y configura el pin IO5 en HIGH.

![](media/A12.png)

5. Arrastra el siguiente bloque en la sección "Control".

![](media/A13.png)

6. Arrastra los siguientes bloques y configura el pin IO5 en LOW.

![](media/A14.png)

**Código Completo：**

![](media/A15.png)

**5. Resultado de la Prueba**

Después de subir el código y encender la alimentación, el LED estará encendido durante 1s y apagado durante 1s.

**6. Explicación del Código**

<p style="color:red;">Nota: El modo del pin debe estar configurado como "output" cuando se use el módulo LED.<p>

1. Los bloques de código no se ejecutarán si no existe el siguiente bloque.

![](media/A16.png)

2. Los bloques de código dentro del siguiente bloque se ejecutarán en un bucle.

![](media/A17.png)

3. Es un módulo usado para configurar el modo del pin (controlar LED y buzzer en modo “output”, y leer el módulo sensor en modo “input”).

![](media/A18.png)

4. Es un módulo usado para configurar el pin y los niveles ("HIGH" y "LOW").

![](media/A19.png)

5. Es un módulo usado para configurar el tiempo de retardo.

![](media/A20.png)