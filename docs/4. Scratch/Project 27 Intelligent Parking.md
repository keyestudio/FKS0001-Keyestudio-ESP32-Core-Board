### Proyecto 27 Estacionamiento Inteligente

**1. Descripción**

Este sistema de estacionamiento inteligente detecta y optimiza la posición de estacionamiento mediante un sensor ultrasónico. Con este sistema, se evita en gran medida el estacionamiento incorrecto.

Primero, debe instalar el sensor alrededor del estacionamiento. Luego, detectará la distancia entre el coche y sus bordes y enviará la información a la placa de desarrollo para controlar que el coche se ajuste automáticamente a la posición óptima de estacionamiento.

**2. Diagrama de Flujo**

![](media/B104.png)

**3. Diagrama de Conexiones**

![](media/B105.png)

**4. Código de Prueba**

Asigne el valor de la distancia detectada a una variable y determine si es mayor que el valor umbral establecido. Si es así, se encenderán las líneas correspondientes en la matriz de puntos. De esta manera, se puede indicar una distancia iluminando líneas.

**Coordenadas de Referencia:**

![](media/B106.png)

**Código Completo:**

![](media/B107.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, se mostrarán líneas en la matriz de puntos. Si la distancia detectada es menor a 50 cm, habrá menos líneas.

![](media/B108.png)![](media/B109.png)