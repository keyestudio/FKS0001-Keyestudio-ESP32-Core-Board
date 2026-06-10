### Proyecto 28 Puerta Inteligente

**1. Descripción**

La puerta inteligente es un sistema de estacionamiento inteligente que integra MCU y sensor ultrasónico, el cual controla automáticamente la puerta según la distancia de los vehículos, para así controlar mejor el acceso de los autos.

Cuando se alcanza cierta distancia, la MCU recibe la señal del sensor y estima la distancia mediante la intensidad de la señal. Si el auto se está acercando o alejando, la MCU abrirá o cerrará la puerta mediante un servo.

**2. Diagrama de Flujo**

![](media/B110.png)

**3. Diagrama de Conexiones**

![](media/B111.png)

**4. Código de Prueba**

Define una variable "distance" con la asignación del valor de distancia detectado por el módulo ultrasónico.

Luego, compara el valor de distancia con 30cm. Si es menor que 30cm, el servo girará a 180° durante 5s. De lo contrario, el servo regresará a 0°.

![](media/B112.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, el servo girará a 180° durante 5s si la distancia detectada es menor a 30cm. Por el contrario, el servo girará a 0°.