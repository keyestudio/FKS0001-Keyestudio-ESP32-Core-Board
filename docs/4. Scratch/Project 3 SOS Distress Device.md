### Proyecto 3 Dispositivo de Socorro SOS

**1. Descripción**

El dispositivo SOS es capaz de emitir señales de socorro, que coinciden con el principio del código Morse. Es conveniente para emergencias.

**2. Diagrama de Conexiones**

![](media/A36.png)

**3. Código de Prueba**

Lo que debemos aclarar primero es cómo parpadea la luz de socorro SOS: el LED parpadea rápidamente 3 veces para la “S” y lentamente 3 veces para la “O”.

Luego, controlamos el número de parpadeos y la duración mediante la instrucción "for" y establecemos el intervalo de tiempo entre letras.

1. Arrastra los dos bloques de código.

![](media/A37.png)

2. Arrastra el siguiente bloque en la sección "Pins" y configura el pin IO5 como salida.

![](media/A38.png)

**Letra "S"**

3. Arrastra el siguiente bloque de la sección "Control" y configúralo para 3 veces, ya que "S" significa parpadear 3 veces.

![](media/A39.png)

4. Arrastra los siguientes bloques de la sección "LED" y configura el pin IO5 en HIGH. Luego establece el tiempo de retardo a 0.15s.

![](media/A40.png)

5. Arrastra los siguientes bloques de la sección "LED" y configura el pin IO5 en LOW. Luego establece el tiempo de retardo a 0.1s.

![](media/A41.png)

**Letra O**

6. Refiérete a los pasos anteriores para construir los siguientes bloques de código. Modifica la salida HIGH para que dure 0.4s y LOW para 0.2s.

![](media/A42.png)

**Letra S**

7. Repite los pasos 3, 4 y 5 nuevamente.

![](media/A43.png)

8. Añade un tiempo de retardo de 5s al final, y el "SOS" se repetirá cada 5s.

   ![](media/A44.png)

**Código Completo：**

![](media/A45.png)

**4. Resultado de la Prueba**

Después de subir el código, el LED parpadea respectivamente 3 veces rápido y luego 3 veces lento.