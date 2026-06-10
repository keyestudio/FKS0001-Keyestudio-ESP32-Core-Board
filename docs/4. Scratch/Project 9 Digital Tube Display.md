### Proyecto 9 Pantalla de Tubo Digital

**1. Descripción**

Esta pantalla de tubo de 4 dígitos es un dispositivo utilizado para mostrar conteos o tiempo, capaz de mostrar números del 0 al 9 y letras simples. Está compuesta por cuatro tubos digitales, cada uno con siete diodos emisores de luz (LED).

Además, se pueden realizar múltiples funciones conectando sus pines a la placa de desarrollo Arduino, como cronometraje y algunos juegos almacenados.

**2. Principio de Funcionamiento**

![](media/A96.png)

TM1650 utiliza el protocolo IIC y adopta dos líneas de bus (SDA y SCL).

El código está proporcionado en nuestros bloques, y el tubo digital mostrará números mediante este código.

**3. Diagrama de Conexiones**

![](media/A97.png)

**4. Código de Prueba**

Para mostrar números en la pantalla, solo necesitas arrastrar un bloque "TM 1650 display" desde "Digital tube" y establecer la cadena numérica en 9999.

![](media/A98.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, la pantalla de tubo digital muestra "9999", como se muestra a continuación.

![](media/A99.png)

**6. Código Extendido**

Vamos a realizar operaciones más complejas. En lugar de números estáticos, haremos que muestre algunos números dinámicos.

El siguiente código manipula los tubos para mostrar del 1 al 9999.

1. Arrastra los dos bloques básicos de código.

![](media/A100.png)

2. Arrastra el siguiente bloque desde "Variables". Establece el tipo en int y el nombre en item, y asigna 0 como valor inicial.

![](media/A101.png)

3. Arrastra el siguiente bloque desde "Control" y configúralo para 9999 repeticiones.

![](media/A102.png)

4. Arrastra un "modo variable" desde "Variables", define su nombre como item y establece el modo en "++".

5. Arrastra un bloque "TM 1650 display" desde "Digital tube" y reemplaza el valor de la cadena con la variable item. Añade un retardo de 0.5s después.

![](media/A103.png)

6. Añade un bloque "set variable" después del bloque "repeat". Establece la variable item en 0. De lo contrario, el valor de item saldrá del rango de visualización después de 9999 ciclos.

![](media/A104.png)

**Código Completo：**

![](media/A105.png)

**7. Explicación del Código**

1. Establece la cadena a mostrar. Escribe directamente los números o letras que deseas mostrar en el espacio en blanco.

![](media/A106.png)

2. Configura el encendido o apagado de este tubo digital TM 1650. Cada tubo puede controlarse por separado.

![](media/A107.png)

3. Es posible limpiar la pantalla o usarlo como interruptor maestro para encender o apagar el tubo digital.

![](media/A108.png)