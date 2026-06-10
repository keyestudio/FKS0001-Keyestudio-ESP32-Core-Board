### Proyecto 11 LCD

**1. Descripción**

El Arduino I2C 1602 LCD es un dispositivo auxiliar comúnmente utilizado para placas de desarrollo MCU para conectar con sensores y módulos externos. Cuenta con una pantalla LCD de 16 caracteres de ancho y 2 líneas, además de brillo ajustable. Este módulo programable es conveniente para la edición, visualización y gestión de datos. Además, puede mostrar no solo caracteres y cifras, sino también valores de sensores, como temperatura, humedad o presión.

Como resultado de su utilidad, la pantalla se aplica ampliamente en muchos campos, incluyendo productos para el hogar inteligente, sistemas de monitoreo industrial, sistemas de control de robots y sistemas electrónicos automotrices.

**2. Principio de Funcionamiento**

![](media/A129.png)

Es el mismo principio de comunicación IIC. Las funciones subyacentes han sido empaquetadas en librerías para que puedas llamarlas directamente. Si te interesa, puedes profundizar en los principios de conducción subyacentes.

**3. Diagrama de Conexiones**

![](media/A130.png)

**4. Código de Prueba**

1. Arrastra los dos bloques básicos de código.

![](media/A131.png)

2. Arrastra el bloque “init LCD” desde “LCD” y configura la dirección I2C a 0x27.

![](media/A132.png)

3. Arrastra el bloque "LCD back light" y configúralo en ON. Los caracteres no son fáciles de leer si no hay luz de fondo.

![](media/A133.png)

4. Arrastra un bloque "LCD cursor position" y configura x en 3 y y en 0. Añade un bloque "LCD print" y escribe “keyestudio” en el espacio en blanco.

![](media/A134.png)

5. Arrastra un bloque "LCD cursor position" y configura x en 2 y y en 1. Añade un bloque "LCD print" y escribe “Hello,world!” en el espacio en blanco.

![](media/A135.png)

**Código Completo：**

![](media/A136.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, enciende el LCD, y se mostrarán en la pantalla "Hello, world!" y "keyestudio!".

Si los caracteres no se ven claros, ajusta el potenciómetro de la luz de fondo con un pequeño destornillador de ranura.

![](media/A137.png)

**6. Explicación del Código**

1. Configura la dirección de comunicación IIC. En este proyecto, la dirección del LCD 1602 es 0x27.

![](media/A138.png)

2. Controla la luz de fondo del LCD. Los caracteres mostrados serán mucho más claros si la luz de fondo está encendida.

![](media/A139.png)

3. Configura la posición del cursor. Proporciona una posición precisa mediante los ejes x e y. Los valores posibles son X: 0-15 y Y: 0-1.

![](media/A140.png)

4. Imprime caracteres en el LCD. El espacio en blanco puede llenarse con caracteres o variables, lo que es conveniente para mostrar valores de sensores y módulos.

![](media/A141.png)

5. Hace parpadear el cursor en la posición de visualización. Por defecto, el cursor está inactivo.

![](media/A142.png)