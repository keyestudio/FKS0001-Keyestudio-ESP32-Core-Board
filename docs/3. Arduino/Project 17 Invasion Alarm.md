### Proyecto 17 Alarma de Invasión

**1. Descripción**

Este sistema de alarma de invasión es capaz de detectar intrusos en casas o pequeñas oficinas y advertir al propietario para que tome medidas a tiempo.

En este proyecto, el sensor monitorea una determinada área. Un dispositivo en la placa Arduino activará un LED para que se encienda y un buzzer para que emita un sonido de advertencia si se detecta movimiento en esa zona.

Prácticamente, este módulo destaca por su practicidad, fácil instalación y bajo costo. Además de aplicarse en hogares y oficinas, también es útil en fábricas, almacenes y mercados, lo que protege en gran medida la seguridad de la propiedad.

**2. Principio de Funcionamiento**

![](media/A64.png)

El cuerpo humano (37°C) siempre emite rayos infrarrojos con una longitud de onda de 10μm, que se aproxima a la que detecta el sensor.

Por esta razón, este módulo es capaz de detectar el movimiento de seres humanos. Si hay movimiento, el sensor PIR emite un nivel alto durante aproximadamente 3 segundos. Si no, emite un nivel bajo.

**3. Diagrama de Conexiones**

![](media/A65.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.1 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;    //Define IO5 como pin del sensor PIR

void setup() 
{
  pinMode(pir,INPUT);   //Configura el pin IO5 como entrada
  Serial.begin(9600);
}

void loop() 
{
  int pir_val = digitalRead(pir); 	//Lee el resultado del PIR y lo asigna a pir_val
    Serial.print("pir_val:"); //Imprime “pir_val”
	Serial.println(pir_val);
    delay(500);
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial y configure la velocidad en 9600 baudios; el puerto serial mostrará el valor del PIR. Si el sensor PIR detecta una persona, mostrará 1.

![](media/A66.png)

**6. Expansión de Conocimientos**

Vamos a hacer una alarma de invasión. Cuando el sensor PIR detecta presencia humana, el LED se enciende y el buzzer emite sonido. En contraste, el LED se apaga y el buzzer permanece en silencio.

- **Diagrama de Flujo：**

![](media/A67.png)

- **Diagrama de Conexiones：**

![](media/A68.png)

- **Código：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.2 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;		//Configura el pin del sensor PIR en IO5
int red_led = 18;	//Configura el LED rojo en el pin IO18
int buzz = 19;		//Configura el buzzer en el pin IO19

void setup() 
{
  // coloca aquí el código de configuración, que se ejecuta una vez:
  pinMode(pir,INPUT);		//Configura el pin PIR en modo entrada
  pinMode(red_led,OUTPUT);	//Configura el pin del LED en modo salida
  pinMode(buzz,OUTPUT);		//Configura el pin del buzzer en modo salida
}

void loop() 
{
  // coloca aquí el código principal, que se ejecuta repetidamente:
  int pir_val = digitalRead(pir);
  if(pir_val == 1)
  {
    digitalWrite(red_led,HIGH);
    digitalWrite(buzz,HIGH);
  }
  else
  {
    digitalWrite(red_led,LOW);
    digitalWrite(buzz,LOW);
  }
}
```

**Resultado de la Prueba**

Si el sensor PIR detecta una persona cerca, el LED rojo se encenderá y el buzzer emitirá sonido.