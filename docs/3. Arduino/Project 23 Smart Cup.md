### Projet 23 Tasse Intelligente

**1. Description**

Dans ce projet, nous utilisons principalement la carte de développement Arduino pour créer une tasse intelligente programmable, qui affiche la température du liquide intérieur via un indicateur RGB. Elle peut contrôler la luminosité de la lumière en réglant un seuil de température. Si le seuil est dépassé, la lumière s’éclaircit. Sinon, elle s’assombrit.

La tasse intelligente permet d’aider les utilisateurs à mieux contrôler la température de leur eau potable et à prévenir efficacement la surchauffe ou la congélation.

**2. Principe de Fonctionnement**

![](media/B23.png)

**3. Schéma de Câblage**

![](media/B24.png)

**4. Code de Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 23.1 Smart Cup
  http://www.keyestudio.com
*/
#include <xht11.h>
xht11 xht(26);   //The DHT11 sensor connects to IO26
unsigned char dat[] = {0,0,0,0}; //Define an array to store temperature and humidity data

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);
}

void loop() 
{
  // put your main code here, to run repeatedly:
  if (xht.receive(dat)) { //Check correct return to true
    Serial.print("RH:");
    Serial.print(dat[0]); //The integral part of humidity,dht[1] is the decimal part
    Serial.print("%  ");
    Serial.print("Temp:");
    Serial.print(dat[2]); //The integer part of the temperature,dht[3] is the decimal part
    Serial.println("C");
  } 
  else 
  {    //Read error
    Serial.println("sensor error");
  }
  delay(1500);  //Delay 1500ms 
}
```

**5. Résultat du Test**

Après avoir connecté le câblage et téléversé le code, ouvrez le moniteur série en réglant le débit en bauds à 9600, et la valeur de température et d’humidité sera affichée.

![](media/B25.png)

**6. Extension des Connaissances**

Maintenant, nous allons réaliser une tasse intelligente capable d’afficher la température du liquide. Nous divisons 100 en quatre parties avec une LED, comme indiqué ci-dessous :

- **LED Rouge :** 100-75°C
- **LED Jaune :** 75-50°C
- **LED Verte :** 50-25°C
- **LED Bleue :** 25-0°C

**Schéma de Câblage :**

![](media/B26.png)

**Code :**

```
/*
  keyestudio ESP32 ESP32 Inventor Learning Kit 
  Project 23.2 Smart Cup
  http://www.keyestudio.com
*/
#include <xht11.h>
xht11 xht(26);                         //Define DHT11 to pin IO26
unsigned char dat[4] = { 0, 0, 0, 0 };  //Define an array to store temperature and humidity data

int red_led = 12;
int yellow_led = 13;   //Define yellow_led to io13
int green_led = 14;    //Define green_led to io14
int blue_led = 27;     //Define blue_led to io27
int temperature = 0;  //Set an variable to save the temperature value

void setup() 
{
  // put your setup code here, to run once:
  pinMode(red_led, OUTPUT);     //Set io12 to ouput 
  pinMode(green_led, OUTPUT);   //Set io13 to ouput 
  pinMode(blue_led, OUTPUT);    //Set io14 to ouput 
  pinMode(yellow_led, OUTPUT);  //Set io27 to ouput 
  Serial.begin(9600);
}

void loop() 
{
  // put your main code here, to run repeatedly:
  if (xht.receive(dat))  //Check correct return to true
  { 
    temperature = dat[2];
    if (temperature > 75) // Determine whether value is greater than 75
    {  
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, HIGH);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,LOW);
    }
    if (temperature < 75 && temperature > 50) //Determine whether value is between 50 and 75 
    {  
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,HIGH);
    }
    if (temperature < 50 && temperature > 25) //Determine whether value is between 25 and 50 
    {  
      digitalWrite(green_led, HIGH);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,LOW);
    }
    if (temperature < 25)  //Determine whether value is smaller than 25 
    { 
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, HIGH);
      digitalWrite(yellow_led,LOW);
    }
  }
  delay(1500);  //Delay 1500ms
}
```

**Résultat du Test**

- **LED Rouge :** 100-75°C
- **LED Jaune :** 75-50°C
- **LED Verte :** 50-25°C
- **LED Bleue :** 25-0°C

Si la LED bleue est allumée, cela signifie que la température détectée par le capteur DHT11 est comprise entre 0 et 25°.