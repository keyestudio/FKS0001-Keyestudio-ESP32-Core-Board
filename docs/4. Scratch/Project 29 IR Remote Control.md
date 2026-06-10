### Proyecto 29 Control Remoto IR

**1. Descripción**

El control remoto IR utiliza señal IR para controlar el LED, lo que simplifica en gran medida el proceso de control del LED.

**2. Principio de Funcionamiento**

![](media/B113.png)

En este proyecto, a menudo usamos un portador de aproximadamente 38K para la modulación.

El sistema de control remoto IR incluye modulación, emisión y recepción. Envía datos mediante modulación, lo que mejora la eficiencia de transmisión y reduce el consumo de energía.

Generalmente, la frecuencia de modulación del portador está dentro de 30kHz~60kHz (usualmente 38kHz). El ciclo de trabajo de la onda cuadrada es 1/3, como se muestra a continuación, lo cual está determinado por el oscilador de cristal de 455kHz en el extremo emisor.  
Una división entera de frecuencia es esencial para el oscilador de cristal en este extremo, y el coeficiente de frecuencia usualmente evalúa 12. Por lo tanto, 455kHz÷12≈37.9kHz≈38kHz.

Diagrama completo de emisión del portador de 38KHz:

![](media/B114.jpg)

- **Frecuencia del portador:** 38KHz

- **Longitud de onda:** 940nm

- **Ángulo de recepción:** 90°

- **Distancia de control:** 6M

**Diagrama esquemático de los botones del control remoto:**

![](media/B115.png)

**3. Diagrama de Conexiones**

![](media/B116.png)

**4. Código de Prueba**

1. Arrastra los dos bloques básicos.

2. Busca y arrastra el bloque "IR remote init" desde “IR Remote” y configura su pin en IO19. Añade un bloque "baud rate" desde "serial" y configúralo a 9600.

![](media/B117.png)、

3. Arrastra un bloque "if" y completa su condición con "Received data". Solo cuando el módulo IR reciba datos, se ejecutarán los bloques de código dentro del "if".

![](media/B118.png)

4. Arrastra otro bloque "if" y configura su condición a "Read the data ＞ 0". Solo cuando esta condición se cumpla, el puerto serial comenzará a imprimir datos.

   Este sensor funciona tan rápido que el código puede ejecutarse dos veces o más mientras presionas los botones de control. Sin embargo, la segunda vez que se envía un mismo comando, se enviará un valor de 0, por lo que es necesario un bloque ">" para evitar duplicaciones.

![](media/B119.png)

5. Añade un bloque "serial print" después de "then". Configúralo para imprimir los datos leídos del módulo "IR remote" en modo "warp".

![](media/B120.png)

6. Finalmente, no olvides refrescar los datos después de la ejecución.

![](media/B121.png)

**Código Completo:**

![](media/B122.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura la tasa de baudios a 9600. Presiona el botón en la unidad del control remoto y verás el valor en hexadecimal.

![](media/B123.png)

**6. Código de Expansión**

En este código de expansión, haremos que una luz sea controlada por un interruptor remoto IR. Presiona OK para encender el LED y presiona nuevamente para apagarlo.

Para realizar esta operación repetible, la variable "item" es esencial en todo el código. La primera vez, item = 0, por lo que se ejecutan los códigos en "else" para asignar 1 como su nuevo valor. La segunda vez, cuando item = 1, sin embargo, se ejecuta el bloque "if" para reasignar a 0, alternativamente.

**Diagrama de Conexiones:**

![](media/B124.png)

**Código:**

![](media/B125.png)

**7. Explicación del Código**

1. Inicializa el módulo remoto IR después de configurar su pin receptor.

![](media/B126.png)

2. Determina si el sensor ha recibido datos. Si es así, se ejecutarán los bloques de código relacionados.

![](media/B127.png)

3. Lee los datos recibidos del control remoto IR.

![](media/B128.png)

4. Refresca los datos recibidos después de cada ejecución completa de recepción.

![](media/B129.png)