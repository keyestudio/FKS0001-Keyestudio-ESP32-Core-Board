### Project 8 Muziekuitvoerder

**1. Beschrijving**

In dit project gebruiken we een versterkerluidspreker om muziek af te spelen. Deze luidspreker kan niet alleen eenvoudige liedjes afspelen, maar ook uitvoeren wat je wenst. Zo kun je andere interessante codes in het project programmeren om schitterende leerresultaten te bereiken.

**2. Werking**

![](media/A28.png)

Het elektrische signaal wordt ingevoerd vanaf pin 1 van RP1 (regelt de signaalsterkte, wat ook het geluidsvolume is).

Na koppeling in C4 en het passeren van R5 bereikt het signaal de IN- pin van 8002B, waar het operationeel wordt versterkt en naar de BEE1 luidspreker wordt uitgegeven.

**Frequentietabel in C**

|    Toon     | Frequentie(Hz) |      Toon      | Frequentie(Hz) |     Toon     | Frequentie(Hz) |
| :---------: | :------------: | :------------: | :------------: | :----------: | :------------: |
| Vlak  1  Do |      262       | Natuurlijk  1  Do |      523       | Kruidig  1  Do |     1047       |
| Vlak  2  Re |      294       | Natuurlijk  2  Re |      587       | Kruidig  2  Re |     1175       |
| Vlak  3  Mi |      330       | Natuurlijk  3  Mi |      659       | Kruidig  3  Mi |     1319       |
| Vlak  4  Fa |      349       | Natuurlijk  4  Fa |      698       | Kruidig  4  Fa |     1397       |
| Vlak  5  So |      392       | Natuurlijk  5  So |      784       | Kruidig  5  So |     1568       |
| Vlak  6  La |      440       | Natuurlijk  6  La |      880       | Kruidig  6  La |     1760       |
| Vlak  7  Si |      494       | Natuurlijk  7  Si |      988       | Kruidig  7  Si |     1967       |

**3. Aansluitschema**

![](media/A29.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 8.1 Music Performer 
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5

void setup() 
{
  pinMode(beeppin, OUTPUT);//Define the IO5 port to output mode 
}

void loop() 
{
  tone(beeppin, 262);//Flat DO plays 500ms
  delay(500);
  tone(beeppin, 294);//Flat Re plays 500ms
  delay(500);
  tone(beeppin, 330);//Flat Mi plays 500ms
  delay(500);
  tone(beeppin, 349);//Flat Fa plays 500ms
  delay(500);
  tone(beeppin, 392);//Flat So plays 500ms
  delay(500);
  tone(beeppin, 440);//Flat La plays 500ms 
  delay(500);
  tone(beeppin, 494);//Flat Si plays 500ms 
  delay(500);
  noTone(beeppin);//Stop for 1s 
  delay(1000);
}
```

**5. Testresultaat**

Na het uploaden van de code en het inschakelen speelt de versterker cirkelvormig muziektonen met de bijbehorende frequenties: DO, Re, Mi, Fa, So, La, Si.

**Geluidregeling van de versterker:**

 **Er zit een potentiometer naast de luidspreker. We kunnen het geluid van de luidspreker regelen door eraan te draaien.** (Opmerking: Gebruik gepaste kracht om te voorkomen dat de potentiometer beschadigd raakt) 

![](media/A30.png)

**6. Kennisuitbreiding**

Laten we een verjaardagsliedje spelen. De bedrading blijft ongewijzigd.

**Genummerde muzieknotatie:**

![](media/A31.png)

**Vergelijkingsdiagram van Vlak, Natuurlijk en Kruidig**

![](media/A32.png)

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 8.2 Music Performer
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5
// do、re、mi、fa、so、la、si

int doremi[] = {262, 294, 330, 370, 392, 440, 494,      //Falt 0-6
                523, 587, 659, 698, 784, 880, 988,      //Natural 7-13
                1047,1175,1319,1397,1568,1760,1967};    //Sharp 14-20
int happybirthday[] = {5,5,6,5,8,7,5,5,6,5,9,8,5,5,12,10,8,7,6,11,11,10,8,9,8};   //Find the number in arrey doremi[] according to the numbered musical notation 
int meter[] = {1,1,2,2,2,4, 1,1,2,2,2,4, 1,1,2,2,2,2,2, 1,1,2,2,2,4};    // Beats

void setup() 
{
  pinMode(beeppin, OUTPUT); //Set IO5 pin to output mode 
}

void loop() 
{
  for( int i = 0 ; i <= 24 ;i++)
  {       //i<=24, because there are only 24 tones in this song
    //Use tone()function to generate a waveform in "frequency"
   tone(beeppin, doremi[happybirthday[i] - 1]);
   delay(meter[i] * 200); //Wait for 1000ms
   noTone(beeppin);//Stop singing
  }
}