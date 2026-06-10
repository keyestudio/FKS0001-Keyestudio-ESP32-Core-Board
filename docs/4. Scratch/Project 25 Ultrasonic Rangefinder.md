### Proyecto 25 Medidor de Distancia Ultrasónico

**1. Descripción**

Este medidor de distancia ultrasónico mide la distancia de obstáculos emitiendo ondas sonoras y luego recibiendo el eco. Es decir, la distancia no es un valor inmediato, sino uno observado mediante un cálculo teórico del tiempo de diferencia entre emisor y receptor.

El ultrasónico es capaz de detectar la forma de objetos, configurar puertas automáticas y estimar la velocidad de flujo y presión.

Además, soporta trabajos cooperativos con computadoras. Como resultado, el valor medido puede ser transmitido a computadoras a través de la placa Arduino.

En la vida diaria, se usa ampliamente para motores, servos y LEDs, así como para sistemas (navegación automática, control y sistemas de monitoreo de seguridad).

**2. Principio de Funcionamiento**

![](media/B91.png)

Como todos sabemos, el ultrasónico es un tipo de señal de onda sonora inaudible con alta frecuencia. Similar a un murciélago, este módulo mide la distancia de obstáculos calculando la diferencia de tiempo entre la emisión de la onda y la recepción del eco.

- **Distancia máxima:** 3M

- **Distancia mínima:** 5cm

- **Ángulo de detección:** ≤15°

**3. Diagrama de Conexiones**

![](media/B92.png)

**4. Código de Prueba**

En el bloque "forever", construya dos bloques "serial print" y arrastre un bloque "read distance" desde “Ultrasonic”. Configure el pin trig en IO13 y el pin echo en IO14, ambos en cm. No olvide un retardo de 0.5s.

![](media/B93.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial para configurar la tasa de baudios a 9600, y el puerto serial comenzará a imprimir el valor de la distancia.

![](media/B94.png)

**6. Ampliación de Conocimientos**

Vamos a hacer un medidor de distancia.

Mostramos caracteres en LCD 1602. Programa para mostrar "Keyestudio" en (3,0) y “distance:” en (0,1) seguido del valor de la distancia en (9,1).

Cuando el valor es menor que 100 (o 10), aún queda un residuo del tercer (o segundo) dígito. Por lo tanto, es necesario un juicio "if" para determinar una condición específica.

**Diagrama de Conexiones：**

![](media/B95.png)

**Código：**

1. Arrastre los dos bloques básicos.

2. En "LCD", inicialice el LCD. Arrastre un bloque “LCD print” y agregue la cadena de caracteres “Keyestudio” (también puede colocarse fuera del bloque "forever" ya que esta pantalla es fija). Agregue un bloque "variable", configure el tipo en int y nombre en "distance" con una asignación inicial de 0.

![](media/B96.png)

3. Asigne el valor leído de la distancia a la variable "distance". Configure el LCD para imprimir “Distance：” seguido del valor de la distancia (y necesitamos calcular previamente los caracteres mostrados al frente para colocar el cursor después de ellos).

![](media/B97.png)

4. Construya un bloque para "borrar residuo de pantalla" cuando disminuya el número de dígitos mostrados. Primero adoptamos una condición para juzgar si la distancia es menor que 100 (o 10). Si es así, se imprimirá un espacio en el residuo del tercer (o segundo) dígito para limpiar la visualización anterior. Por último, no olvide agregar un retardo de 0.5s.

![](media/B98.png)

**Código Completo:**

![](media/B99.png)

**7. Explicación del Código**

Lea la distancia después de configurar el pin trig y el pin echo. La unidad del valor mostrado es opcional (cm o pulgada).

![](media/B100.png)