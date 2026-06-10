### Proyecto 16 Bomba de Tiempo

**1. Descripción**

Este proyecto te dará la oportunidad de experimentar un interesante juego de bomba de tiempo.

En este proyecto, la matriz de puntos representa tu bomba de tiempo, mientras que el tubo digital muestra el tiempo restante. Los botones no solo pueden controlar la bomba, sino también configurar su tiempo. Puedes establecer una cuenta regresiva para controlar esta bomba, y esta explota cuando la cuenta termina. Además, se utiliza un zumbador para la alarma.

De cualquier manera, al programar con múltiples sensores, tu capacidad integral de pensamiento lógico puede ser mejorada.

**2. Diagrama de Flujo**

![](media/B1.png)

**3. Diagrama de Conexiones**

![](media/B2.png)

**4. Código de Prueba**

1. Arrastra los dos bloques básicos.

![](media/B3.png)

2. Configura el pin del botón como “input”.

![](media/B4.png)

3. Añade un bloque "init matrix display" desde "Matrix" y configura el pin CS a IO15. A continuación, un bloque "brightness" con valor 3 y un bloque "variable" (configura el tipo de variable a int y el nombre a item, asignando 0 como valor inicial).

![](media/B5.png)

4. En "Matrix", arrastra un bloque "fill color" y selecciona "black" (es decir, todos los LED se apagan para limpiar la pantalla anterior). Añade un bloque "display image" para definir una cara sonriente. Luego, coloca un bloque de refresco para actualizar la pantalla.

![](media/B6.png)

5. Arrastra un bloque "if" y llena el cuadro de condición con "interface IO33 button was be pushed?". Añade un bloque "variable mode" después de "then" y configura su nombre a item y modo a "++".

![](media/B7.png)

6. Repite la operación del paso 5, pero configura la interfaz a IO32 y el modo a "--".

![](media/B8.png)

7. Arrastra un bloque "if" para evaluar si el pin IO26 está presionado. Dentro de este "if", añade un bloque repeat y configura su condición a "item" = 0.

En el bucle "repeat until", coloca un bloque "variable mode" y configura "item" a "--", como se muestra abajo. Arrastra un bloque "TM1650 display" desde "Digital tube" y define la cadena mostrada como el bloque "variable item". Luego añade un bloque "buzzer output" y configura la salida a HIGH en el pin IO27 seguido de un retardo de 0.5s. Repite el último procedimiento pero configura la salida a LOW.

![](media/B9.png)

8. Programa otro código de bucle y define la condición como "interface IO25 button was be pushed?". Las siguientes ejecuciones están dentro de este bucle. Coloca un bloque "TM1650 display" y define la cadena mostrada como el bloque "variable item". Luego repite el paso 4 pero aquí configuramos la imagen a una cara llorando.

![](media/B10.png)

9. Arrastra un bloque "if then" y llena el espacio en blanco con la condición: item ＞ 9999. Añade una instrucción "set item variable by 0" dentro de este bloque condicional.

![](media/B11.png)

10. Arrastra un bloque "TM1650 display" desde "Digital tube" y define la cadena mostrada como "variable item". Igualmente, no olvides un retardo de 0.2s.

![](media/B12.png)

**Código Completo:**

![](media/B13.png)

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, presiona el botón azul para aumentar el tiempo, el verde para reducirlo y el rojo para reiniciar. Presiona el botón amarillo para iniciar la cuenta regresiva. Cuando esta termina, la bomba explota.