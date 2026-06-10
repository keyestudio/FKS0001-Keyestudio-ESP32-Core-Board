### Proyecto 15 Respondedor

**1. Descripción**

Este respondedor programable recibe y envía señales a través de la placa de desarrollo Arduino y un grupo de botones, y juzga la corrección de las respuestas mediante un LED. Es un buen objeto para ejercitar la capacidad de reacción de los estudiantes y captar su atención hacia las preguntas. Si la respuesta es correcta, el participante obtiene muchos puntos.

Además, simplifica la manipulación de los capturadores de preguntas por parte de los profesores y reduce el desorden de respuestas. Incluso puede estimular el interés de los estudiantes por el aprendizaje.

**2. Diagrama de flujo**

![](media/A184.png)

**3. Diagrama de conexiones**

![](media/A185.png)

**4. Código de prueba**

1. Arrastra los dos bloques básicos y coloca un bloque de "variable" entre ellos. Configura el tipo de variable a int y nómbrala como item con una asignación inicial de 0. Configura el pin del LED como “output” y el pin del botón como “input”.

![](media/A186.png)

2. Añade un bloque de "LED output", define su pin en IO27 y configura la salida en HIGH.  
3. Arrastra un bloque "if" y añade la condición "interface IO19 button was be pushed?".

![](media/A187.png)

4. Añade una asignación de variable y cuatro bloques de salida LED bajo "then". Entre ellos, nombramos la variable "item" con una asignación de "0", y configuramos todas las salidas en LOW respectivamente en los pines 12, 13, 14 y 27 (El respondedor funciona solo cuando todos los LEDs están apagados). Asimismo, no olvides un retardo de 0.2s.

![](media/A188.png)

5. Añade un bloque "repeat until" y configura el "until" a "item = 1", como se muestra a continuación. Cuando item = 1, se sale del bucle.

![](media/A189.png)

6. Arrastra otro bloque "if" y configura la condición "Interface IO16 button was be pushed?". Añade un bloque "LED output" bajo "then" y configura la salida en HIGH en el pin IO12. Y añade un "set item variable by 1" para salir de este bloque condicional.

![](media/A190.png)

7. Repite el paso 6, pero configura la interfaz en IO17 y el pin del LED en IO13.

![](media/A191.png)

8. Repite el paso 6 nuevamente, pero configura la interfaz en IO18 y el pin del LED en IO14.

![](media/A192.png)

**Código completo:**

![](media/A193.png)

**5. Resultado de la prueba**

Conecta el cableado y sube el código. Las respuestas de los participantes solo son válidas cuando el LED rojo está apagado (el botón rojo está presionado).

Cuando alguien presiona su botón (amarillo, verde o azul), el LED correspondiente así como el rojo se encienden. En este momento, el resto de los LEDs no pueden encenderse al presionar botones. La acción de respuesta solo puede realizarse cuando se presiona nuevamente el botón rojo.

**6. Explicación del código**

1. Módulo de bucle condicional. Cuando se cumplen las condiciones en el recuadro de diamante del módulo, el bucle se termina.

![](media/A194.png)

2. El bloque "=" se usa para juzgar si dos valores son iguales.

![](media/A195.png)