### **Proyecto 13 Mini Lámpara**

**1. Descripción**

En este proyecto, vamos a controlar una lámpara mediante Arduino UNO y un botón. Cuando presionamos el botón, el estado de la lámpara cambiará (ENCENDIDO o APAGADO).

**2. Principio de Funcionamiento**

![](media/A53.png)

Cuando el botón está liberado, un voltaje VCC que pasa a través de R29 proporciona un nivel alto para el terminal S. Cuando se presiona, los pines 1 y 3, y los pines 2 y 4 se conectan y el voltaje en S1 llega a GND como un nivel bajo. En este momento, R29 evita un cortocircuito entre VCC y GND.

**3. Diagrama de Conexiones**

![](media/A54.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.1 Mini Lamp
  http://www.keyestudio.com
*/
int button = 15;
int value = 0;

void setup() 
{
  Serial.begin(9600); //Establece la velocidad en baudios del puerto serial a 9600 
  pinMode(button, INPUT);  //Conecta el pin del botón al puerto digital 8 y configúralo en modo entrada.
}

void loop() 
{
  value = digitalRead(button);//Lee el valor del botón 
  Serial.print("Key status:"); //Imprime "Key status:" en el puerto serial 
  Serial.println(value); //Imprime la variable del botón en el puerto serial y hace salto de línea
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura la velocidad en baudios a 9600.  
Cuando presionamos el botón, el puerto serial imprime "Key status: 0"; cuando lo soltamos, el puerto serial imprime "Key status: 1".

![](media/A55.png)

**6. Ampliación de Conocimientos**

A continuación, controlaremos el LED mediante el estado de los botones.

- **Diagrama de Flujo：**

![](media/A56.png)

- **Diagrama de Conexiones:**

![](media/A57.png)

- **Código**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 13.2 Mini Lamp
  http://www.keyestudio.com
*/
#define led	   4
#define button 15
bool ledState = false;

void setup() 
{
  // inicializa el pin digital PIN_LED como salida.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT);
}

// la función loop se ejecuta repetidamente para siempre
void loop() 
{
  if (digitalRead(button) == LOW) {    //Cuando el valor del botón es 0 por primera vez, se activa el rebote del botón, por lo que se retrasa 20ms para juzgar si el botón sigue siendo 0. 
    delay(20);                              //Retraso de 20ms
    if (digitalRead(button) == LOW) {   //juzga si el valor del botón es 0
      ledState = !ledState;                 //ledState es igual al inverso de su valor original, lo que permite encender y apagar el LED 
      digitalWrite(led, ledState);
    }
    while (digitalRead(button) == LOW);     //mantiene el botón presionado en el bucle while, sale cuando se suelta
  }
}
```

- **Resultado de la Prueba**

Puedes controlar el encendido y apagado del LED rojo mediante el botón rojo.