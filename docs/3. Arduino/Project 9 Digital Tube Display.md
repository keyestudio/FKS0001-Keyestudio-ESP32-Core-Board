### Projekt 9 Digitalrohr-Anzeige

**1. Beschreibung**

Diese 4-stellige Rohranzeige ist ein Gerät zur Anzeige von Zählwerten oder Zeit, das Zahlen von 0 bis 9 sowie einfache Buchstaben darstellen kann. Sie besteht aus vier Digitalrohren, von denen jedes sieben Leuchtdioden (LED) enthält.

Darüber hinaus können durch Anschluss der Pins an das Arduino-Entwicklungsboard mehrere Funktionen realisiert werden, wie z.B. Zeitmessung und einige Spielespeicherungen.

**2. Funktionsprinzip**

![](media/A33.png)

Der TM1650 verwendet das IIC-Protokoll und nutzt zwei Busleitungen (SDA und SCL).

**Datenbefehl:** 0x48.  
Dieser Befehl weist den TM1650 an, die Digitalrohre einzuschalten, anstatt die Tastenabfrage durchzuführen.

**Anzeige-Befehl:**

![](media/A34.png)

Tatsächlich handelt es sich um ein Datenbyte, bei dem verschiedene Bits unterschiedliche Funktionen repräsentieren.  
**bit[6:4]:** Legt die Helligkeit der LED fest. Beachten Sie, dass 000 die höchste Helligkeit bedeutet.  
**bit[3]:** Bestimmt, ob ein Dezimalpunkt angezeigt wird.  
**bit[0]:** Bestimmt, ob die Anzeige eingeschaltet wird.

**Digitalrohr einschalten**  
Beispiel: Helligkeitsstufe 8 ohne Punkt entspricht 0x05.  
Ablauf: Startsignal — Sende 0x48 — Slave-Gerät empfängt — Sende 0x05 — Slave-Gerät empfängt — Endsignal  
Nach dem Einschalten muss 0x48 nicht wiederholt gesendet werden, da die Funktion des Digitalrohrs bestätigt ist.  
Außerdem können Helligkeit und Anzeigemodus mit mehreren Daten an einer Stelle aufgelistet werden, was übersichtlich und platzsparend ist.

**Digitalrohr ausschalten**  
Ablauf: Startsignal — Sende 0x48 — Slave-Gerät empfängt — Sende 0x00 — Slave-Gerät empfängt — Endsignal

**Digitalrohr zeigt Zahlen an**  
Zuerst wird dem TM1650 mitgeteilt, auf welchem Rohr die Zahl angezeigt werden soll. Danach wird die Zahl dargestellt. Das 8-Bit-Datenbyte entspricht acht Segmenten, wobei 1 für eingeschaltet und 0 für ausgeschaltet steht. Bei Unsicherheiten bezüglich der Zuordnung kann man die Bits einzeln in einer Schleife einschalten.

Beispielsweise entspricht das Einschalten von Bit 1 und die Anzeige der 8 dem Wert 0x68. Wenn ein Punkt vorhanden ist, wird die 8 auch bei Senden von 0x7f angezeigt.  
Ablauf: Startsignal — Sende 0x68 — Slave-Gerät empfängt — Sende 0x7f — Slave-Gerät empfängt — Endsignal  
Ergebnis: 8 wird auf Bit 1 angezeigt.

Zur Vereinfachung kann ein Array mit den entsprechenden Werten für 0 bis 9 erstellt werden. Nach weiteren Verbesserungen ist es möglich, Zahlen anzuzeigen, die Helligkeit anzupassen, den Dezimalpunkt zu verschieben und die Rohre zu steuern.

**3. Schaltplan**

![](media/A35.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.1 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
    DigitalTube.displayFloatNum(9999);   //Values or variables added to the parentheses can be displayed through the digital tube 
}
```

**5. Testergebnis**

Nach Anschluss der Verkabelung und Hochladen des Codes zeigt die Digitalrohr-Anzeige „9999“ an, wie unten dargestellt.

![](media/A36.png)

**6. Erweiterter Code**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.2 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  for(int num=0; num<10000; num++)
  {   //Wenn num kleiner als 10000 ist, wird num in jedem Zyklus um 1 erhöht
    DigitalTube.displayFloatNum(num);   //Werte oder Variablen in den Klammern können über das Digitalrohr angezeigt werden
    delay(100);
  }
}
```

**7. Testergebnis**

Nach dem Hochladen des Codes zeigt das Digitalrohr die Zahlen von 1 bis 9999 in einer „for“-Schleife an.