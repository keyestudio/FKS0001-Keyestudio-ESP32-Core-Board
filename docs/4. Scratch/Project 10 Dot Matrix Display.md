### Proyecto 10 Pantalla de Matriz de Puntos

**1. Descripción**

Este módulo consiste en una matriz de puntos LED de 8x8 con un pin de control para cada fila y cada columna para ajustar el brillo del LED. Conectado a una placa Arduino, el brillo del LED se controla para mostrar caracteres y figuras mediante programación en Arduino. De esta manera, se pueden mostrar caracteres simples, números y figuras. También puede aplicarse en máquinas de juego o pantallas.

![](media/A109.png)

MAX7219 es un CI con comunicación SPI que puede usarse para controlar la matriz de puntos 8x8. La comunicación SPI del MAX7219 está integrada en nuestras librerías y puedes llamarla directamente.

**2. Diagrama de Conexiones**

![](media/A110.png)

**3. Código de Prueba**

1. Arrastra los dos bloques básicos de código.

![](media/A111.png)

2. Arrastra un bloque "init matrix display" desde “Matrix” y configura CS en IO15. DIN y CLK son pines fijos respectivamente en IO23 e IO18.

![](media/A112.png)

3. Arrastra un bloque "set brightness" y configúralo en 3.

![](media/A113.png)

4. Arrastra un bloque "image" y elige el icono de corazón.

![](media/A114.png)

5. Añade un bloque "refresh" al final.

![](media/A115.png)

**Código Completo：**

![](media/A116.png)

**4. Resultado de la Prueba**

Después de conectar el cableado y subir el código, se mostrará un corazón en la matriz de puntos, como se muestra a continuación.

![](media/A117.png)

**5. Explicación del Código**

1. Configura el pin CS. En el código, DIN está fijo en io23 y SLK en io18, mientras que el pin CS es opcional. Para facilitar el cableado, seleccionamos io15.

![](media/A118.png)

2. Dibujar píxeles. Este bloque de código encenderá o apagará píxeles en la matriz de puntos según los ejes x e y, con rojo para encendido y negro para apagado.

![](media/A119.png)

3. Dibujar línea. Ubica la línea mediante dos grupos de puntos de coordenadas, también con rojo para encendido y negro para apagado.

![](media/A120.png)

4. Mostrar caracteres. Hemos añadido librerías de caracteres, por lo que solo necesitas escribir una letra para mostrarla en la matriz de puntos. Además, debe usarse conjuntamente con un bloque "rotation 180°".

![](media/A121.png)

5. Mostrar números. De manera similar, solo necesitas escribir un número para mostrarlo en la matriz de puntos, y también debe usarse conjuntamente con un bloque "rotation 180°".

![](media/A122.png)

6. Mostrar cadenas de caracteres desplazándose. Colocando un bloque "rotation 180°", las cadenas de texto desplazadas especificadas se mostrarán después de configurar su velocidad.

![](media/A123.png)

7. Mostrar imagen. Para mayor comodidad, ya hemos integrado algunos iconos de emociones que pueden seleccionarse directamente.

![](media/A124.png)

8. Mostrar colores de relleno. Puedes configurar en negro (LED apagado) o rojo (LED encendido).

![](media/A125.png)

9. Refrescar la pantalla. La matriz de puntos debe refrescarse si muestra algo. De lo contrario, puede ocurrir un error.

![](media/A126.png)

10. Ajustar el brillo. Puedes bajar el brillo durante la depuración para evitar molestias a tus ojos.

![](media/A127.png)

11. Ajustar ángulos de rotación. Para alta compatibilidad con más código, algunos datos e iconos necesitan una rotación para evitar una visualización invertida. Por eso es necesario un bloque "rotation 180°" en los códigos.

![](media/A128.png)