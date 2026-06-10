### Proyecto 5 Luz Ambiental Arcoíris

**1. Descripción**

El LED 2812RGB es una luz programable, colorida y soñadora, cuyo color, brillo y ritmo son ajustables. Esta luz ambiental arcoíris puede usarse como una decoración dinámica a voluntad. O puede controlarse para "bailar con la música". Lo importante es que puede mejorarse como una alarma. Su sensor incorporado detecta el entorno ambiental para advertir a los usuarios cambiando su color, brillo y ritmo.

**2. Principio de Funcionamiento**

![](media/A53.png)

El protocolo de datos adopta un modo de comunicación de código de retorno a cero por línea única. Después de que el píxel se reinicia al encenderse, el terminal DIN recibe datos del controlador. Los primeros 24 bits de datos que llegan serán extraídos por el primer píxel y enviados al registro interno de datos.

Los datos restantes serán amplificados por un circuito amplificador y transmitidos a través del puerto DOUT al siguiente píxel en cascada.  
Al transmitirse a través de los píxeles, la señal disminuye 24 bits cada vez.

Además, el píxel adopta tecnología de conformado y reenvío automático, de modo que el número en cascada de píxeles está limitado solo por la velocidad de transmisión de la señal.

**3. Diagrama de Conexiones**

![](media/A54.png)

**4. Código de Prueba**

Aprendamos cómo encender el 2812 RGB y configurar sus colores.

1. Arrastra los dos bloques de código.

![](media/A55.png)

2. Arrastra el siguiente bloque de la sección "RGB LED" y configura el pin en IO15 y el número de LED en 6.

![](media/A56.png)

3. Arrastra el siguiente bloque de la sección "RGB LED" y ajusta el brillo a 20.

![](media/A57.png)

4. Arrastra los siguientes bloques y configura el número de LED en 0, 1, 2, 3, 4 y 5, luego elige los colores rojo, verde, azul, amarillo, púrpura y blanco.

![](media/A58.png)

5. Añade el siguiente bloque.

![](media/A59.png)

**Código Completo:**

![](media/A60.png)

**5. Resultado de la Prueba**

Después de subir el código, conectar el cableado y encender, el LED se iluminará en diferentes colores, como se muestra a continuación:

![](media/A61.png)

**6. Ampliación de Conocimientos**

En este proyecto de ampliación, ¡hagamos un mini espectáculo de luces!

Anida cuatro bloques de "repetir" y añade un "variable +" en ellos, luego limpia las variables correspondientes a 0 al final de cada ciclo.

![](media/A62.png)

Coloca las tres variables anteriores en el bloque "RGB" para que estos valores de color sean controlados. Luego añade un módulo de actualización.

![](media/A63.png)

Coloca el RGB en un bloque "mostrar color" para desplegar colores. Y define una variable item para controlar el LED mostrado.

![](media/A64.png)

El módulo forever se usa para controlar los LEDs RGB, que ciclarán de 0 a 5 para encender gradualmente cada luz.

![](media/A65.png)

**Código Completo**

![](media/A66.png)

**7. Explicación del Código**

1. Configura el número de 2812 RGB. Un pin de la placa de desarrollo puede controlar múltiples LEDs 2812 RGB, por lo que necesitamos establecer el número de antemano y seleccionar el pin conectado.

![](media/A67.png)

2. Configura el brillo del 2812 RGB. Ingresa un valor de brillo entre 0 y 255, donde 255 es el más brillante.

![](media/A68.png)

3. Este bloque apagará todos los 2812 RGB.

![](media/A69.png)

4. Controla la visualización de los 2812 RGB. Podemos rellenar los espacios para controlar el LED que se enciende y su color después de seleccionar el pin. Por ejemplo, "0 a 0" significa que solo se enciende el primer LED. Después de subir el código, el primer LED se encenderá en el color configurado.

**NOTA:** Los dos espacios también pueden llenarse con variables, para que se pueda formar un espectáculo de luces.

![](media/A70.png)

5. Configura el color de los 2812 RGB. El color mostrado puede modularse con los valores de rojo, verde y azul. Podemos añadir este bloque en la configuración de color del 2812 RGB.

![](media/A71.png)

6. Puede controlar un solo 2812 RGB ingresando el número del LED a controlar y seleccionando el color.

![](media/A72.png)

7. El 2812 RGB mostrará el color configurado solo después de actualizar.

![](media/A73.png)