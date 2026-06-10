### Proyecto 18 Corazón Palpitante

**1. Descripción**

En este proyecto, se presentará un corazón palpitante mediante una placa Arduino, una pantalla de matriz de puntos 8X8, una placa de circuito y algunos componentes electrónicos. Mediante programación, puedes controlar la frecuencia de los latidos, la dimensión del corazón y su brillo.

**2. Diagrama de Conexiones**

![](media/B24.png)

**3. Código de Prueba**

1. Arrastra los dos bloques básicos.

2. Inicializa la pantalla de matriz de puntos. Configura el pin CS en IO15 y su brillo en 3. Coloca estas dos ejecuciones entre los bloques básicos.

Las siguientes ejecuciones están todas dentro del bloque "forever".

3. Limpia la pantalla. Controla la pantalla para dibujar líneas y establecer el sistema de coordenadas y su origen como se muestra a continuación. Luego, actualiza la pantalla para mostrar el corazón pequeño con un retardo de 1s.

![](media/B25.png)

![](media/B26.png)

4. Repite el paso 3 pero dibuja las líneas como en la imagen siguiente para mostrar un corazón más grande.

![](media/B27.png)

![](media/B28.png)

**Código Completo:**

![](media/B29.png)

**4. Resultado de la Prueba**

Después de conectar el cableado y subir el código, los dos tamaños de corazones se muestran de forma alternada.

![](media/B30.png)![](media/B31.png)