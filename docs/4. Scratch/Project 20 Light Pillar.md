### Proyecto 20 Pilar de Luz

**1. Descripción**

La resistencia (menos de 1KΩ) de la fotorresistencia varía según la luz, por lo que puede controlar el brillo de la matriz de puntos. Al controlar, conectamos esta resistencia a un pin analógico en la placa para monitorear el cambio de resistencia. De esta manera, la luz controla automáticamente el brillo de la pantalla.

Además, la fotorresistencia se aplica ampliamente en nuestra vida diaria. Por ejemplo, una cortina se abre o cierra automáticamente según la intensidad de la luz exterior.

**2. Principio de Funcionamiento**

![](media/B43.png)

Cuando está completamente en oscuridad, la resistencia es igual a 0.2MΩ, y el voltaje en el terminal de señal (punto 2) se acerca a 0V. Cuanto más fuerte es la luz, menor será la resistencia y el voltaje.

**3. Diagrama de Conexiones**

![](media/B44.png)

**4. Código de Prueba**

Se puede leer el valor analógico de la fotorresistencia:

1. Arrastra los dos bloques básicos. Coloca el bloque de configuración de baud rate entre ellos y configúralo a 9600.

2. Añade un bloque de "serial print" dentro del bucle "forever" con el modo "warp".

3. Arrastra un bloque de "read the value" desde “Light” al bloque de "serial print", y configura el pin a IO33.

![](media/B45.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura el baud rate a 9600, se mostrará el valor analógico dentro del rango de 0-4095.

![](media/B46.png)

**6. Código de Expansión**

En este proyecto de expansión, usamos esta fotorresistencia para detectar la intensidad de luz ambiental. Las dos columnas centrales están incluidas en este experimento para representar la intensidad de luz. Cuanto más claro esté, más LEDs se encenderán. Esto forma un "pilar de luz".

**Diagrama de Conexiones:**

![](media/B47.png)

1. Arrastra los dos bloques básicos.

2. En "Matrix", inicializa la pantalla de matriz de puntos y configura el pin CS a IO15. Añade un bloque de "brightness setting" y asígnale el valor 3.

![](media/B48.png)

3. Arrastra un bloque de "variable". Configura su alcance a Local, tipo a int y nómbralo light.

![](media/B49.png)

4. Asigna una función map a la variable. Añade "read the value of light IO33" desde "Light" al valor de la función map, cuyo rango es de (0,4095) a (0,7).

![](media/B50.png)

5. Encuentra los siguientes bloques en "Matrix". Limpia primero la pantalla, y luego dibuja líneas en la pantalla en los puntos (x0:3  y0:0, x1:3  y1: variable light) y (x0:4  y0:0, x1:4  y1: variable light). Finalmente, actualiza la pantalla de la matriz.

![](media/B51.png)

**Código Completo:**

![](media/B52.png)

**7. Explicación del Código**

Lee el valor analógico de la fotorresistencia configurando el pin.

![](media/B53.png)