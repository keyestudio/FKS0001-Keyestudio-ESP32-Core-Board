### Proyecto 24 Estación Meteorológica

**1. Descripción**

Esta estación meteorológica registra la temperatura y humedad ambiental mediante una placa Arduino y un sensor de temperatura y humedad.

Además, permite ajustar los valores de temperatura y humedad según los parámetros ambientales como una forma de lograr condiciones ambientales confortables.

**2. Diagrama de Conexiones**

![](media/B84.png)

**3. Código de Prueba**

1. Añade dos módulos básicos. Inicializa el LCD 1602 y enciende la luz de fondo del LCD 1602 (recuerda activar el LCD). Configura el pin del dht en IO26 y el modo en dht11. Declara dos variables int llamadas “RH“ y “temp“ con valor 0.

![](media/B85.png)

2. Asigna el valor de humedad a la variable RH, y el valor de temperatura a la variable temp.

![](media/B86.png)

3. Establece la posición de la pantalla LCD en x: 0 y y: 0. Añade el módulo de visualización lcd y configura el texto a mostrar como "humidity:". Añade nuevamente el módulo de visualización lcd y agrega la variable RH en el recuadro blanco.

![](media/B87.png)

4. Repite el paso 3, pero configura y : 1 y el texto a mostrar como “temperature:” y agrega la variable temp en el recuadro blanco.

![](media/B88.png)

**Código Completo:**

![](media/B89.png)

**4. Resultado de la Prueba**

Después de conectar el cableado y subir el código, la pantalla LCD mostrará directamente el valor de humedad y temperatura ambiental.

![](media/B90.png)