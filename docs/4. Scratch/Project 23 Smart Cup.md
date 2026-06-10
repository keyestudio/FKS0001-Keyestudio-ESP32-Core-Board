### Proyecto 23 Vaso Inteligente

**1. Descripción**

En este proyecto, utilizamos principalmente la placa de desarrollo Arduino para crear un vaso inteligente programable, que muestra la temperatura del líquido interno mediante un indicador RGB. Puede controlar el brillo de la luz configurando un umbral de temperatura. Si se supera el umbral, la luz se vuelve más brillante. De lo contrario, se atenúa.

El vaso inteligente ayuda a los usuarios a controlar mejor la temperatura de su agua para beber y previene eficazmente el sobrecalentamiento o la congelación.

**2. Principio de Funcionamiento**

![](media/B71.png)

Las configuraciones relacionadas con el DHT11 son proporcionadas por los fabricantes, por lo que solo necesitas leer y procesar los datos de forma ordenada según su diagrama de secuencia.

Además, los códigos relevantes están empaquetados en nuestras librerías, lo que facilita configurar los pines y leer los valores.

**3. Diagrama de Conexiones**

![](media/B72.png)

**4. Código de Prueba**

1. Arrastra dos bloques básicos. Añade el módulo de velocidad de baudios serial y configura la velocidad a 9600.

2. Arrastra el módulo DHT desde “Temperatura y humedad” y configura el pin en IO26, modo en dht11.

![](media/B73.png)

3. Añade el módulo de impresión serial sin salto de línea, y configura la impresión en “RH:”, luego sigue los pasos siguientes y añade un retardo de 1s.

**Código Completo:**

![](media/B74.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, haz clic ![](media/B75.png) para abrir el monitor serial, configura la velocidad de baudios a 9600, y se mostrarán los valores de temperatura y humedad.

![](media/B76.png)

**6. Código de Expansión**

En este experimento de expansión, haremos un vaso inteligente que puede mostrar la temperatura del líquido. Dividimos 100 en cuatro partes con un LED representando cada una:

- **LED Rojo:** 100-75°C

- **LED Amarillo:** 75-50°C

- **LED Verde:** 50-25°C

- **LED Azul:** 25-0°C

- **Diagrama de Flujo：**

![](media/B77.png)

**Diagrama de Conexiones：**

![](media/B78.png)

**Código：**

1. Arrastra dos bloques básicos. Luego configura los 4 pines de los LED como “output”, el pin del DHT11 en IO26, modo en dht11 y el nombre de la variable como temp.

![](media/B79.png)

2. Asigna el valor de temperatura del DHT11 a la variable temp.

![](media/B80.png)

3. Usa el bloque "if else" para evaluar la variable temp. Si se cumplen las condiciones, el LED correspondiente se encenderá, de lo contrario se apagará.

**Código Completo:**

![](media/B81.png)

**7. Explicación del Código**

1. En este bloque de código, el número marcado puede rellenarse en el espacio en blanco para conectar múltiples sensores de temperatura y humedad. Después de configurar el pin y el modo, se puede leer el valor. En este proyecto, configuramos el modo en DHT11.

![](media/B82.png)

2. Bloque de código para leer la temperatura y humedad.

![](media/B83.png)