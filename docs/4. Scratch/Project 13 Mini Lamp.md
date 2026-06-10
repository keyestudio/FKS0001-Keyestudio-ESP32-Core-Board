### Proyecto 13 Mini Lámpara

**1. Descripción**

En este proyecto, vamos a controlar una lámpara mediante Arduino UNO y un botón. Cuando presionamos el botón, el estado de la lámpara cambiará (ENCENDIDO o APAGADO).

**2. Principio de Funcionamiento**

![](media/A152.png)

Cuando el botón está suelto, un voltaje VCC que pasa a través de R29 proporciona un nivel alto para el terminal S. Cuando se presiona, los pines 1 y 3, y los pines 2 y 4 se conectan y el voltaje en S1 llega a GND como un nivel bajo. En este momento, R29 evita un cortocircuito entre VCC y GND.

**3. Diagrama de Conexiones**

![](media/A153.png)

**4. Código de Prueba**

1. Añade dos bloques básicos.

![](media/A154.png)

2. Arrastra un bloque "baud rate" de “Serial” y configúralo a 9600.

![](media/A155.png)

3. Luego arrastra un bloque "print" de “Serial”, escribe “Key status:” en el espacio en blanco y configúralo en "no-warp".

![](media/A156.png)

4. Configura el pin IO15 como “input”.

![](media/A157.png)

5. Arrastra otro bloque “Serial print” de “Serial” y configura el modo a "warp". Añade un bloque "state value of button" de “Button” y configura el pin a IO15.

![](media/A158.png)

**Código Completo:**

![](media/A159.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura la velocidad en baudios a 9600.  
Cuando presionamos el botón, el puerto serial imprime "Key status: 0"; cuando soltamos el botón, el puerto serial imprime "Key status: 1".

![](media/A160.png)

**6. Expansión de Conocimientos**

A continuación, controlaremos el LED a través del estado de los botones.

**Diagrama de Flujo：**

![](media/A161.png)

**Diagrama de Conexiones：**

![](media/A162.png)

**Código:**

1. Arrastra dos bloques básicos.

![](media/A163.png)

2. Configura el pin del LED como “output” y el pin del botón como “input”.

![](media/A164.png)

3. Arrastra un bloque "if else" de “Control”. Añade un bloque "button pin" de “Button” después de "if" y configura su pin a IO15. Coloca un bloque "LED output" debajo de "if" y configúralo a HIGH, y coloca otro debajo de "else" y configúralo a LOW. Los pines del LED son ambos IO4.

![](media/A165.png)

**Código Completo:**

![](media/A166.png)

**8. Explicación del Código**

**Nota: El modo del pin debe configurarse como "input" cuando se usa el módulo de botón.**

1. Se evalúa si el botón está presionado. Si es así, este bloque devuelve verdadero.

![](media/A167.png)

2. Lee el valor del botón. Cuando el botón no está presionado, el valor es 1. De lo contrario, es 0.

![](media/A168.png)

3. Si la condición en el hexágono es verdadera, se ejecuta el bloque "if". De lo contrario, el programa ejecuta el bloque "else".

![](media/A169.png)

4. Configura la velocidad en baudios. Por favor, asegúrate de que la velocidad en baudios del serial coincida con la del monitor serial, o no imprimirá nada. Las velocidades en baudios comúnmente usadas son 9600 y 115200, aquí configuramos a 9600.

![](media/A170.png)

5. Imprime caracteres en el monitor serial. Las palabras impresas son las que escribes en el espacio en blanco. Además, se incluyen tres modos de impresión: warp, no-warp y HEX (hexadecimal).

![](media/A171.png)