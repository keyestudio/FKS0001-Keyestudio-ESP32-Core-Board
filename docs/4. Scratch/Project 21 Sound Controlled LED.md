### Proyecto 21 LED Controlado por Sonido

**1. Descripción**

El LED controlado por sonido es un dispositivo utilizado para detectar sonido de manera que controla el brillo del LED, compuesto por una placa Arduino y algunos componentes. Puede conectarse a múltiples sensores como micrófonos. Convierte el sonido en una señal de voltaje variable que es recibida por Arduino para controlar el encendido y apagado del LED.

**2. Principio de Funcionamiento**

![](media/B54.png)

Al detectar un sonido, la película electret en el micrófono vibra, lo que cambia la capacitancia y genera un cambio sutil de voltaje.

Luego, utilizamos el chip LM386 para construir un circuito adecuado que amplifique el sonido detectado hasta 200 veces, lo cual puede ajustarse mediante un potenciómetro. Gírelo en sentido horario para aumentar la amplificación.

**3. Diagrama de Conexiones**

![](media/B55.png)

**4. Código de Prueba**

Encuentre el bloque "leer el valor" en “Sound” y imprima el sonido leído en el puerto serial. Construya los bloques como se muestra a continuación. Preste atención a no agregar un retardo al usar el sensor de sonido.

![](media/B56.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial y configure la tasa de baudios a 9600, el valor analógico se mostrará.

![](media/B57.png)

**6. Código de Expansión**

La luz de pasillo comúnmente vista es un tipo de luz controlada por sonido. Además, incluye una fotorresistencia.

A diferencia de eso, aquí establecemos un modelo en el que un LED solo es afectado por el sonido. Cuando el volumen analógico supera 100, el LED se enciende durante 2 segundos y luego se apaga.

**Diagrama de Flujo：**

![](media/B58.png)

**Diagrama de Conexiones：**

![](media/B59.png)

**Código：**

1. Arrastre dos bloques básicos.

2. Arrastre un bloque "if else" y llene el hexágono con un bloque item＞100. Configure el valor a "leer el valor de sonido IO33". Si la condición se cumple, el LED emite un nivel ALTO en el pin IO25 con un retardo de 2s; de lo contrario, emite un nivel BAJO en el mismo pin sin retardo.

![](media/B60.png)

**Código Completo:**

![](media/B61.png)

**7. Explicación del Código**

Lee el valor del sonido configurando el pin relacionado.

![](media/B62.png)Proyecto 22 Medidor de Ruido

**1. Descripción**

El medidor de ruido Arduino representa la señal de sonido en una serie de puntos, que se convierten en patrones mostrados en una matriz de puntos.

**2. Diagrama de Conexiones**

![](media/B63.png)

**3. Código de Prueba**

1. Arrastre los bloques básicos e inicialice la pantalla. Configure el pin CS a IO15 y el brillo a 3. Luego agregue un bloque de variable, seleccione int y nómbrelo como "item" con una asignación inicial de 0.

2. Agregue un bloque de variable y nómbrelo "item". Use una función map para convertir el rango del valor de sonido leído de 0-4095 a 0-7, asumiendo que el valor máximo hipotético del sonido es 800.

![](media/B64.png)

3. Limpie la pantalla.

4. Programe una condición. Si la variable item es mayor que -1, la matriz de puntos muestra (x0:0  y0:0 x1:1  y1:0) en color rojo.

![](media/B65.png)

5. Repita el paso 4, pero la condición es si item es mayor que 0. Si es así, se encenderán los puntos en (x0:1  y0:0  x1:1  y1:1). Por analogía, construya bloques de código refiriéndose a las siguientes coordenadas.

6. Finalmente, actualice la pantalla.

**Coordenadas de Referencia:**

![](media/B66.png)

![](media/B67.png)

**Código Completo:**

![](media/B68.png)

**4. Resultado de la Prueba**

Después de conectar el cableado y subir el código, el nivel de ruido se muestra en la matriz de puntos, como se muestra a continuación.