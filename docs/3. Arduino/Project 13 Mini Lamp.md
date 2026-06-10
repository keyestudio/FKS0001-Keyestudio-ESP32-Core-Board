### **Project 13 Mini Lamp**

**1. Beschrijving**

In dit project gaan we een lamp bedienen via Arduino UNO en een knop. Wanneer we de knop indrukken, verandert de status van de lamp (AAN of UIT).

**2. Werkingsprincipe**

![](media/A53.png)

Wanneer de knop wordt losgelaten, zorgt een spanning VCC die door R29 loopt voor een hoog niveau op de S-terminal. Wanneer de knop wordt ingedrukt, zijn pin 1 en 3, pin 2 en 4 verbonden en komt de spanning op S1 op GND als een laag niveau. Op dat moment voorkomt R29 een kortsluiting tussen VCC en GND.

**3. Aansluitschema**

![](media/A54.png)

**4. Testcode**

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
  Serial.begin(9600); //Stel de seriële baudrate in op 9600 
  pinMode(button, INPUT);  //Verbind de knop met digitale poort 8 en stel deze in als input.
}

void loop() 
{
  value = digitalRead(button);//Lees de waarde van de knop 
  Serial.print("Key status:"); //Print "Key status:" op de seriële poort 
  Serial.println(value); //Print de knopvariabele op de seriële poort en ga naar de volgende regel
}
```

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code, open je de seriële monitor en stel je de baudrate in op 9600.  
Wanneer we de knop indrukken, print de seriële poort "Key status: 0"; wanneer we loslaten, print de seriële poort "Key status: 1".

![](media/A55.png)

**6. Kennisuitbreiding**

Vervolgens gaan we de LED bedienen via de status van de knoppen.

- **Stroomschema:**

![](media/A56.png)

- **Aansluitschema:**

![](media/A57.png)

- **Code**

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
  // initialiseer digitale pin PIN_LED als uitgang.
  pinMode(led, OUTPUT);
  pinMode(button, INPUT);
}

// de loop-functie draait continu oneindig door
void loop() 
{
  if (digitalRead(button) == LOW) {    //Wanneer de knopwaarde voor het eerst 0 is, wordt knopdebouncing geactiveerd, dus wordt 20ms gewacht om te controleren of de knop nog steeds 0 is. 
    delay(20);                              //Wacht 20ms
    if (digitalRead(button) == LOW) {   //controleer of de knopwaarde 0 is
      ledState = !ledState;                 //ledState wordt het tegenovergestelde van de oorspronkelijke waarde, wat gebruikt kan worden om de LED aan en uit te zetten 
      digitalWrite(led, ledState);
    }
    while (digitalRead(button) == LOW);     //houd de knop ingedrukt in de while-lus, verlaat deze wanneer de knop wordt losgelaten
  }
}
```

- **Testresultaat**

Je kunt de rode LED aan- en uitzetten met de rode knop.