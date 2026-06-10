### Project 15 Responder

**1. Beschrijving**

Deze programmeerbare responder ontvangt en verzendt signalen via een Arduino-ontwikkelbord en een groep knoppen, en beoordeelt de juistheid van antwoorden via een LED. Het is een goed hulpmiddel om de reactievermogen van studenten te oefenen en hun aandacht op vragen te richten. Als het antwoord correct is, krijgt de respondent veel punten.

Bovendien vereenvoudigt het de bediening van vraaggrijpers door docenten en vermindert het de rommel van antwoorden. Het kan zelfs de interesse van studenten in leren stimuleren.

**2. Stroomschema**

![](media/A184.png)

**3. Aansluitschema**

![](media/A185.png)

**4. Testcode**

1. Sleep de twee basisblokken en plaats een "variabele" blok ertussen. Stel het variabeltype in op int en de naam op item met een initiële toewijzing van 0. Stel de LED-pin in op “output” en de knop-pin op “input”.

![](media/A186.png)

2. Voeg een "LED output" blok toe, definieer de pin als IO27 en zet de output op HIGH.  
3. Sleep een "if" blok en voeg de voorwaarde toe "interface IO19 button was be pushed?".

![](media/A187.png)

4. Voeg een variabele instelling en vier LED output blokken toe onder "then". Noem de variabele "item" met een toewijzing van "0", en zet alle outputs respectievelijk op LOW bij pin 12, 13, 14 en 27 (de responder werkt alleen wanneer alle LED’s uit zijn). Vergeet ook niet een vertraging van 0,2s.

![](media/A188.png)

5. Voeg een "repeat until" blok toe en stel "until" in op "item = 1", zoals hieronder weergegeven. Wanneer item = 1, verlaat de lus.

![](media/A189.png)

6. Sleep nog een "if" blok en stel de voorwaarde in op "Interface IO16 button was be pushed?". Voeg een "LED output" blok toe onder "then" en zet de output op HIGH bij pin IO12. Voeg ook een "set item variable by 1" toe om deze conditie te verlaten.

![](media/A190.png)

7. Herhaal stap 6, maar stel interface in op IO17 en LED-pin op IO13.

![](media/A191.png)

8. Voer stap 6 opnieuw uit, maar stel interface in op IO18 en LED-pin op IO14.

![](media/A192.png)

**Volledige code:**

![](media/A193.png)

**5. Testresultaat**

Sluit de bedrading aan en upload de code. De antwoorden van respondenten zijn alleen geldig wanneer de rode LED uit is (rode knop is ingedrukt).

Wanneer iemand zijn/haar knop indrukt (geel, groen of blauw), gaan de bijbehorende LED en de rode LED aan. Op dat moment kunnen de andere LED’s niet aangaan bij het indrukken van knoppen. De responsactie kan alleen worden uitgevoerd wanneer de rode knop opnieuw wordt ingedrukt.

**6. Code-uitleg**

1. Conditielusmodule. Wanneer de voorwaarden in het diamantvormige vak van de module zijn voldaan, verlaat de lus.

![](media/A194.png)

2. Het "=" blok wordt gebruikt om te beoordelen of de twee waarden gelijk zijn.

![](media/A195.png)