### Proyecto 17 Alarma de Invasión

**1. Descripción**

Este sistema de alarma de invasión es capaz de detectar intrusos en casas o pequeñas oficinas y advertir al propietario para que tome medidas a tiempo.

En este proyecto, el sensor monitorea una determinada área. Un dispositivo en la placa Arduino activará un LED para que se encienda y un buzzer para que emita un sonido de advertencia si se detecta movimiento en esa zona. Además, su sensibilidad es ajustable para una detección más precisa.

Prácticamente, este módulo se caracteriza por su practicidad, fácil instalación y bajo costo. Además de aplicarse en hogares y oficinas, también es útil en fábricas, almacenes y mercados, lo que protege en gran medida la seguridad de la propiedad.

**2. Principio de Funcionamiento**

![](media/B14.png)

El cuerpo humano (37°C) siempre emite rayos infrarrojos con una longitud de onda de 10μm, que se aproxima a la que detecta el sensor.

Por esta razón, este módulo es capaz de detectar el movimiento de seres humanos. Si lo hay, el sensor PIR emite un nivel alto durante aproximadamente 3 segundos y luego emite un nivel bajo.

**3. Diagrama de Conexiones**

![](media/B15.png)

**4. Código de Prueba**

1. Añade los dos bloques básicos y arrastra un bloque de "baud rate" desde “Serial” entre ellos. Configura la velocidad en baudios del puerto serial a 9600.

![](media/B16.png)

2. Añade un bloque "if else". Coloca un bloque "read PIR motion sensor" en el recuadro hexagonal y configura la interfaz en IO5, así determinará si hay movimiento humano. Añade dos bloques "serial print" después de "then" y "else" y configura ambos modos en "warp". Si la condición se cumple, imprime “Someone Invaded”. De lo contrario, imprime “No one”, luego añade un retardo de 1s.

![](media/B17.png)

**Código Completo:**

![](media/B18.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y ajusta la velocidad en baudios a 9600. Cuando el sensor detecta movimiento, el puerto serial imprime "Someone Invaded", de lo contrario, imprime “No One”.

![](media/B19.png)

**6. Código de Expansión**

Vamos a crear una alarma de invasión. Cuando el sensor PIR detecta presencia humana, el LED se enciende y el buzzer emite sonido. En contraste, el LED se apaga y el buzzer permanece en silencio.

**Diagrama de Flujo：**

![](media/B20.png)

**Diagrama de Conexiones：**

![](media/B21.png)

**Código：**

![](media/B22.png)

**7. Explicación del Código**

Cuando el PIR detecta movimientos humanos, emite un nivel alto. Por lo tanto, podemos determinar si hay movimiento leyendo el pin de la placa de desarrollo conectado a este sensor.

![](media/B23.png)