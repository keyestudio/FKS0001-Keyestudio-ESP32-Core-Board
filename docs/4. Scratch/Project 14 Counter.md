### Proyecto 14 Contador

**1. Descripción**

El contador de tubo digital de 4 bits Arduino puede registrar números dentro del rango 0~9999. Cuenta con ajuste de velocidad de visualización, modo de conteo y función de reinicio. Este módulo se aplica ampliamente en contadores en tiempo real (como conteo de pulsaciones de botón y rotación de motor DC), juegos y equipos de experimentación.

**2. Diagrama de flujo**

![](media/A172.png)

**3. Diagrama de conexiones**

![](media/A173.png)

**4. Código de prueba**

1. Arrastra los dos bloques básicos.

![](media/A174.png)

2. Configura el pin del botón como “input”.

![](media/A175.png)

3. Coloca un bloque de "variable". Establece el tipo de variable como int y nómbrala como item. Asigna 0 como su valor inicial.

![](media/A176.png)

4. Arrastra un bloque "if" desde “Control” (se ejecuta solo cuando su condición se cumple). Coloca un bloque “Button pressed” desde “Button” en el cuadro de condición (el hexágono) y configura el pin en IO19. Arrastra un bloque "variable mode" y colócalo después de "then", definiéndolo como "item" y establece el modo en "++".

![](media/A177.png)

5. Repite el paso 4, pero configura la interfaz en IO18 y el modo en "– –".

![](media/A178.png)

6. Arrastra otro bloque "if" desde “Control” y define su condición como "¿se presionó el botón de la interfaz IO17?". Coloca un bloque de configuración de variable después de "then" y establece la variable en 0.

![](media/A179.png)

7. Arrastra un bloque "if" desde “Control”. Busca el bloque "＞" en “Operators” y rellena el espacio izquierdo con la "variable item" y el derecho con "9999". Además, coloca un bloque de configuración de variable después de "then" y establece la variable en 0.

![](media/A180.png)

8. Arrastra un bloque "TM1650 display" desde "Digital tube" y configura la cadena mostrada con el bloque "variable item". Finalmente, no olvides añadir un retardo de 0.2s.

![](media/A181.png)

**Código completo:**

![](media/A182.png)

**5. Resultado de la prueba**

Después de conectar el cableado y subir el código, presiona el botón verde para sumar 1, el amarillo para restar 1 y el rojo para reiniciar.

**6. Explicación del código**

El bloque **">"** se usa para comparar dos valores. Estos dos espacios pueden ser reemplazados por números o variables.

![](media/A183.png)