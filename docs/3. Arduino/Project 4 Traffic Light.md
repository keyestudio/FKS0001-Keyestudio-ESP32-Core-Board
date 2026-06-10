### Proyecto 4 Semáforo

**1. Descripción**

El módulo de semáforo es un dispositivo utilizado para controlar el paso de peatones y vehículos. Incluye una luz roja, una amarilla y una verde, que implican diferentes instrucciones.

**Rojo para Detenerse:** Peatones y vehículos deben detenerse.

**Amarillo para Precaución:** Peatones y vehículos deben prepararse para detenerse. Si la conducción ya está en proceso, la velocidad debe ser lenta.

**Verde para Avanzar:** Peatones y vehículos continúan respetando las normas de tráfico.

En este proyecto, puedes usar Arduino para escribir código que controle los semáforos. Por ejemplo, establecer la duración de cada luz y el intervalo entre ellas. Además, también puedes añadir un temporizador para alterar los colores de las luces según un horario.

**2. Diagrama de Conexiones**

![](media/A21.png)

**3. Código de Prueba**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 4 Traffic Light
  http://www.keyestudio.com
*/
int greenPin = 27;   //Green LED connects to IO27
int yellowPin = 26; //Yellow LED connects to IO26
int redPin = 25;   //Red LED connects to IO25

void setup() 
{
  //Set all LED interfaces to output mode
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(redPin, OUTPUT);
}

void loop() 
{
  digitalWrite(greenPin, HIGH); //Light green LED up 
  delay(5000);  //Delay 5s
  digitalWrite(greenPin, LOW); //Turn green LED off 
  for (int i = 1; i <= 3; i++) //Execute for 3 times
  {  
    digitalWrite(yellowPin, HIGH); //Light yellow LED up
    delay(500); //Delay 0.5s
    digitalWrite(yellowPin, LOW); // Turn yellow LED off
    delay(500); //Delay 0.5s
  }
  digitalWrite(redPin, HIGH); //Light red LED up 
  delay(5000);  //Delay 5s 
  digitalWrite(redPin, LOW); //Turn red LED off 

}
```

**4. Resultado de la Prueba**

Después de subir el código, el LED verde se encenderá durante 5s, el LED amarillo parpadeará 3 veces y el LED rojo se encenderá durante 5s, en ciclo continuo.
