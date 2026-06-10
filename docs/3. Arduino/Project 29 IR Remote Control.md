### Project 29 IR Afstandsbediening

**1. Beschrijving**

De IR afstandsbediening gebruikt een IR-signaal om een LED te bedienen, wat het proces van het aansturen van de LED aanzienlijk vereenvoudigt.

**2. Werking**

![](media/B41.png)

In dit project gebruiken we vaak een draaggolf van ongeveer 38K voor modulatie.

Het IR-afstandsbedieningssysteem omvat modulatie, uitzenden en ontvangen. Het verzendt data door modulatie, wat de transmissie-efficiëntie verbetert en het energieverbruik vermindert.

Over het algemeen ligt de frequentie van de draaggolfmodulatie tussen 30kHz en 60kHz (meestal 38kHz). De duty cycle van de vierkante golf is 1/3, zoals hieronder weergegeven, wat wordt bepaald door de 455kHz kristaloscillator aan de zendzijde.

Een gehele frequentiedeling is essentieel voor de kristaloscillator aan deze kant, en de frequentiefactor is meestal 12. Daarom is 455kHz ÷ 12 ≈ 37,9kHz ≈ 38kHz.

**38KH draaggolf (volledig) zenddiagram:**

![](media/B42.jpg)

**Draaggolffrequentie:** 38KHz

**Golflengte:** 940nm

**Ontvangshoek:** 90°

**Bedieningsafstand:** 6M

**Schema van afstandsbedieningsknoppen:**

![](media/B43.png)

**3. Aansluitschema**

![](media/B44.png)

**4. Testcode**

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

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600.

Druk op een knop van de afstandsbediening en je ziet de waarde in hexadecimale notatie.

![](media/B45.png)

**6. Kennisuitbreiding**

Vervolgens gebruiken we een IR-afstandsbediening om de LED te bedienen. Druk op OK om de LED aan te zetten en druk nogmaals om deze uit te schakelen.

**Aansluitschema：**

![](media/B46.png)

**Code：**

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

**Testresultaat:** 

Druk op OK om de LED aan te zetten en druk nogmaals om deze uit te schakelen.