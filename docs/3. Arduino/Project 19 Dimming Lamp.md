### Proyecto 19 Lámpara Regulable

**1. Descripción**

La lámpara regulable ajusta el brillo del LED mediante un potenciómetro y un controlador Arduino. El brillo depende del valor de resistencia, que puede ser leído y ajustado conectando los extremos del potenciómetro a pines digitales o analógicos en la placa. Además, este sistema se aplica para controlar el voltaje o la corriente de otros dispositivos como ventiladores, bombillas y calentadores.

**2. Principio de Funcionamiento**

![](media/B3.png)

![](media/B4.png)

Esencialmente, el potenciómetro es un elemento que puede cambiar el valor de la resistencia. Según la ley de Ohm (U=I*R), la resistencia afecta el voltaje. Nuestro potenciómetro es de 10K.

En este proyecto, la resistencia máxima es de 10K. La placa ESP32 dividirá igualmente el voltaje de 3V en 4095 partes (3/4095=0.0007326007326). El voltaje analógico se obtiene multiplicando el valor leído por 0.0007326007326.

**3. Diagrama de Conexiones**

![](media/B5.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.1 Dimming Lamp
  http://www.keyestudio.com
*/
int pot = 34;      //Define variable pot a IO34

void setup() 
{
  // pon aquí el código de configuración, que se ejecuta una vez:
  Serial.begin(9600);		//Configura la tasa de baudios a 9600
}

void loop() 
{
  // pon aquí el código principal, que se ejecuta repetidamente:
  int value = analogRead(pot);	//Lee io34 y asigna el valor a la variable value
  Serial.println(value);		//Imprime la variable value y hace salto de línea
  delay(200);
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abre el monitor serial y configura la tasa de baudios a 9600, y se mostrará el valor analógico dentro del rango de 0-4095. Girar el potenciómetro puede cambiar el tamaño del valor analógico.

![](media/B6.png)

**6. Ampliación de Conocimientos**

Controlaremos el brillo del LED mediante un potenciómetro. Como sabemos, esto está influenciado por PWM. Sin embargo, el rango del valor analógico es 0-4095 mientras que el de PWM es 0-255. Por lo tanto, se necesita una función "map(value, fromLow, fromHigh, toLow, toHigh)".

**Diagrama de Conexiones：**

![](media/B7.png)

**Código：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.2 Dimming Lamp
  http://www.keyestudio.com
*/
int led = 25;		//Define LED a IO25
int pot = 34;		//Define pot a IO34

void setup() 
{
  // pon aquí el código de configuración, que se ejecuta una vez:
  pinMode(led,OUTPUT);		//Configura el pin LED como salida
}

void loop() 
{
  // pon aquí el código principal, que se ejecuta repetidamente:
  int value = analogRead(pot);
  int led_val = map(value,0,4095,0,255);  //Convierte el rango del valor analógico del potenciómetro al rango que necesitamos  
  analogWrite(led,led_val);
}
```

**7. Resultado de la Prueba**

Después de subir el código con éxito, girar el potenciómetro cambiará el brillo del LED rojo.