### Proyecto 12 Servo

**1. Descripción**

Este servo ofrece un alto rendimiento y alta precisión con un ángulo máximo de rotación de 180°. Con un peso de solo 9g, es perfectamente adecuado para cualquier dispositivo mini en múltiples ocasiones. Además, cuenta con un tiempo de arranque corto, bajo ruido y gran estabilidad.

**2. Principio de Funcionamiento**

**Rango de ángulo:** 180° (360°, 180° y 90°)

**Voltaje de alimentación:** 3.3V o 5V

**Pin:** Tres cables

![](media/A143.png)

**GND:** Tierra (marrón)

**VCC:** Un pin rojo que se conecta a una alimentación de +5V (3.3V)

**S:** Un pin de señal naranja controlado mediante señal PWM

![](media/A144.png)

**Principio de Control**: El ángulo de rotación se controla mediante el ciclo de trabajo del PWM. Teóricamente, el ciclo estándar de PWM es de 20ms (50Hz), por lo que el ancho de pulso debe distribuirse entre 1ms y 2ms. Sin embargo, el ancho de pulso real alcanza de 0.5ms a 2.5ms, lo que corresponde a 0° a 180°. Preste atención a que, para la misma señal, el ángulo de rotación puede variar según la marca del servo.

**3. Diagrama de Conexiones**

![](media/A145.png)

**4. Código de Prueba**

1. Arrastre los dos bloques básicos y coloque un bloque de "variable" entre ellos. Configure el tipo de variable a int, nombre a angle, y asigne 0 como valor inicial.

![](media/A146.png)

2. **El servo rota gradualmente de 0° a 180°:** 

Agregue un bloque de repetir y establezca las repeticiones en 180 (180 ángulos). Arrastre un bloque de "cambiar variable" y un bloque de "servo" y colóquelos dentro del bloque de repetir. Nombre la variable "angle" y seleccione el modo "++". Configure el PIN del Servo en IO4 y el grado en la variable nombrada. No olvide retrasar 15 ms.

![](media/A147.png)

3. **El servo rota gradualmente de 180° a 0°:** Repita el paso 2, pero configure el modo de la variable en "--".

![](media/A148.png)

**Código Completo：**

![](media/A149.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y cargar el código, el servo comienza a rotar de 0° a 180° y luego de 180° a 0°.

**6. Explicación del Código**

1. Establece los valores del Servo. El pin del servo y el ángulo de rotación pueden controlarse configurando los parámetros en este bloque.

![](media/A150.png)

2. Lee el grado actual del Servo.

![](media/A151.png)