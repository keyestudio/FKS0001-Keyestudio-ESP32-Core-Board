### Proyecto 21 LED Controlado por Sonido

**1. Descripción**

El LED controlado por sonido es un dispositivo utilizado para detectar sonido de manera que controla el brillo del LED, el cual está compuesto por una placa Arduino y algunos componentes. Puede conectarse a múltiples sensores como micrófonos. Convierte el sonido en una señal de voltaje variable que es recibida por Arduino para controlar el encendido y apagado del LED.

**2. Principio de Funcionamiento**

![](media/B14.png)

Al detectar un sonido, la película electret en el micrófono vibra, lo que cambia la capacitancia y genera un cambio sutil de voltaje.

A continuación, utilizamos el chip LM3 para construir un circuito adecuado que amplifique el sonido detectado, el cual puede ajustarse mediante un potenciómetro. Gírelo en sentido horario para aumentar la amplificación.

**3. Diagrama de Conexiones**

![](media/B15.png)

**4. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.1：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33; //Define sound as IO33

void setup()
{
  Serial.begin(9600);
  pinMode(sound,INPUT);
}

void loop()
{
  int value = analogRead(sound);
  Serial.println(value);
}
```

**5. Resultado de la Prueba**

Después de conectar el cableado y subir el código, abra el monitor serial y configure la tasa de baudios a 9600, se mostrará el valor analógico.

![](media/B16.png)

**Ajuste de sensibilidad:**

Si considera que la sensibilidad del sensor de sonido es adecuada, podemos ajustar el potenciómetro del sensor de sonido (hacia la derecha para la sensibilidad más alta, hacia la izquierda para la sensibilidad más baja).

![](media/B17.png)

**6. Ampliación de Conocimientos**

La luz de pasillo comúnmente vista es un tipo de luz controlada por sonido. Además, incluye una fotorresistencia. A diferencia de eso, aquí establecemos un modelo en el que un LED solo es afectado por el sonido. Cuando el volumen analógico supera 100, el LED se enciende durante 2 segundos y luego se apaga.

- **Diagrama de Flujo:**

![](media/B18.png)

- **Diagrama de Conexiones:**

![](media/B19.png)

- **Código:**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 21.2：Sound Controlled LED
  http://www.keyestudio.com
*/
int sound = 33;   //Define sound to IO33
int led = 25;      //Define led to IO25

void setup()
{
  pinMode(led,OUTPUT);   //Set IO25 to output 
}

void loop()
{
  int value = analogRead(sound);    //Read analog value of IO33 and assign it to value
  if(value > 100)
  {                  //Judge whether value is greater than 100
    digitalWrite(led,HIGH);         //If IO25 pin outputs high level, LED lights up
    delay(2000);
  }
  else
  {
    digitalWrite(led,LOW);          //If IO25 pin outputs low level, LED lights off
  }
}
```

- **Resultado de la Prueba**

Cuando el valor detectado por el sensor de sonido es mayor que 100, el LED rojo se encenderá.