### Proyecto 22 Medidor de Ruido

**1. Descripción**

El medidor de ruido Arduino representa la señal de sonido en una serie de puntos, que se convierten en patrones mostrados en la matriz de puntos.

**2. Diagrama de Conexiones**

![](media/B63.png)

**3. Código de Prueba**

1. Arrastra los bloques básicos e inicializa la pantalla. Configura el pin CS en IO15 y el brillo en 3. Luego añade un bloque de variable, selecciona int y nómbralo como "item" con una asignación inicial de 0.

2. Añade un bloque de variable y nómbralo como "item". Usa una función map para convertir el rango del valor de sonido leído de 0-4095 a 0-7, considerando que el valor máximo hipotético del sonido es 800.

![](media/B64.png)

3. Limpia la pantalla.

4. Programa una condición. Si la variable item es mayor que -1, la matriz de puntos mostrará (x0:0  y0:0 x1:1  y1:0) en color rojo.

![](media/B65.png)

5. Repite el paso 4, pero la condición será si item es mayor que 0. Si es así, se encenderán los puntos en (x0:1  y0:0  x1:1  y1:1). Por analogía, construye bloques de código refiriéndote a las siguientes coordenadas.

6. Finalmente, actualiza la pantalla.

**Coordenadas de Referencia:**

![](media/B66.png)

![](media/B67.png)

**Código Completo:**

![](media/B68.png)

**4. Resultado de la Prueba**

Después de conectar el cableado y subir el código, el nivel de ruido se muestra en la matriz de puntos, como se muestra a continuación.

![](media/B69.png)![](media/B70.png)![](media/B69.png)![](media/B70.png)