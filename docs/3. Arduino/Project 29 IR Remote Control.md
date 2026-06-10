### Projet 29 Télécommande IR

**1. Description**

La télécommande IR utilise un signal IR pour contrôler la LED, ce qui simplifie grandement le processus de contrôle de la LED.

**2. Principe de fonctionnement**

![](media/B41.png)

Dans ce projet, nous utilisons souvent un porteuse d’environ 38K pour la modulation.

Le système de télécommande IR comprend la modulation, l’émission et la réception. Il envoie des données par modulation, ce qui améliore l’efficacité de transmission et réduit la consommation d’énergie.

Généralement, la fréquence de modulation porteuse est comprise entre 30kHz et 60kHz (habituellement 38kHz). Le rapport cyclique de l’onde carrée est de 1/3, comme illustré ci-dessous, ce qui est déterminé par le quartz oscillateur à 455kHz côté émission.

Une division entière de fréquence est essentielle pour le quartz oscillateur à ce niveau, et le coefficient de fréquence est généralement évalué à 12. Par conséquent, 455kHz÷12≈37,9kHz≈38kHz.

**Schéma d’émission complet de la porteuse 38KH :**

![](media/B42.jpg)

**Fréquence porteuse :** 38KHz

**Longueur d’onde :** 940nm

**Angle de réception :** 90°

**Distance de contrôle :** 6M

**Schéma des boutons de la télécommande :**

![](media/B43.png)

**3. Schéma de câblage**

![](media/B44.png)

**4. Code de test**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 29.1 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

const uint16_t recvPin = 19;  // Infrared receiving pin
IRrecv irrecv(recvPin);  // Create a class object used to receive class
decode_results results;   // Create a decoding results class object
long ir_rec;

void setup()
{
  Serial.begin(9600); // Initialize the serial port and set the baud rate to 9600
  irrecv.enableIRIn(); // start receiving signals
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value; //assign the signal to the variable ir_rec
    if(ir_rec != 0)
    {		//Prevente the code from repeating execute when the button is pressed 
        Serial.print(ir_rec, HEX); //Print the variable ir_rec in hexadecimal
        Serial.println();//Wrapping lines
    }
    irrecv.resume(); //Release the IR remote and receive the next value.
  }
} 
```

**5. Résultat du test**

Après avoir connecté le câblage et téléversé le code, ouvrez le moniteur série et réglez le débit en bauds à 9600.

Appuyez sur un bouton de la télécommande, et vous verrez la valeur en hexadécimal.

![](media/B45.png)

**6. Extension des connaissances**

Ensuite, nous allons utiliser une télécommande IR pour contrôler la LED. Appuyez sur OK pour allumer la LED et appuyez de nouveau pour l’éteindre.

**Schéma de câblage :**

![](media/B46.png)

**Code :**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 29.2 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

int led = 25;
int led_val = 0;
const uint16_t recvPin = 19;  // Infrared receiving pin
IRrecv irrecv(recvPin);       // Create a class object used to receive class
decode_results results;       // Create a decoding results class object
long ir_rec;

void setup() 
{
  Serial.begin(9600);   // Initialize the serial port and set the baud rate to 9600
  irrecv.enableIRIn();  // start receiving signals
  pinMode(led, OUTPUT);
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value;      //assign the signal to the variable ir_rec
    if (ir_rec != 0) 
    {           //Prevente the code from repeating execute when the button is pressed
      if (ir_rec == 0xFF02FD) //Determine whether the received IR signal is from button OK
      {  
        led_val = !led_val;      //Reverse a variable. If the initial value is 0, it turns to 1 after reversing  
        digitalWrite(led, led_val);
      }
    }
    irrecv.resume();  //Release the IR remote and receive the next value.
  }
}
```

**Résultat du test :**

Appuyez sur OK pour allumer la LED et appuyez de nouveau pour l’éteindre.