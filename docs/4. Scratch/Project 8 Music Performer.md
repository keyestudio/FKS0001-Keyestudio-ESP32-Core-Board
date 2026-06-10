### Proyecto 8 Intérprete Musical

**1. Descripción**

En este proyecto, utilizaremos un altavoz con amplificador de potencia para reproducir música. Este altavoz no solo puede reproducir canciones simples, sino también interpretar lo que desees. Por lo tanto, puedes programar otros códigos interesantes en el proyecto para lograr resultados de aprendizaje espléndidos.

**2. Principio de Funcionamiento**

![](media/A89.png)

La señal eléctrica se introduce desde el pin 1 de RP1 (ajusta la intensidad de la señal, que también es el volumen del sonido).  
Después de acoplarse en C4 y pasar por R5, la señal llega al pin IN- del 8002B, donde se amplifica operativamente y se envía al altavoz BEE1.

**3. Diagrama de Conexiones**

![](media/A90.png)

**4. Código de Prueba**

![](media/A91.png)

**5. Resultado de la Prueba**

Después de cargar el código y encender, el amplificador reproduce circularmente tonos musicales con la frecuencia correspondiente: DO, Re, Mi, Fa, So, La, Si.

**6. Ampliación de Conocimientos**

Hagamos que reproduzca una canción de cumpleaños. Ya hemos añadido algunas canciones en la biblioteca para que puedas arrastrar directamente estos bloques de canción desde "Music".

**Código:**

![](media/A92.png)

**7. Explicación del Código**

1. Establecer la frecuencia del tono. Después de configurar el pin, podemos seleccionar la frecuencia para componer música.

![](media/A93.png)

2. Módulo de música, para facilitar su uso, hemos integrado 6 piezas musicales en el código, por lo que solo necesitamos configurar el pin y seleccionar la música.

![](media/A94.png)

3. Módulo de detención de reproducción, solo necesitamos configurar el pin correspondiente para detener la música.

![](media/A95.png)