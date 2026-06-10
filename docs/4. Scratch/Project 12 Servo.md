### Project 12 Servo

**1. Beschrijving**

Deze servo heeft een hoge prestatie en hoge precisie met een maximale rotatiehoek van 180°. Met een gewicht van slechts 9g is hij perfect geschikt voor elk mini-apparaat in diverse toepassingen. Bovendien heeft hij een korte opstarttijd, weinig geluid en sterke stabiliteit.

**2. Werking**

**Hoekbereik:** 180° (360°, 180° en 90°)

**Voedingsspanning:** 3.3V of 5V

**Pin:** Drie draden

![](media/A143.png)

**GND:** Aarde (bruin)

**VCC:** Een rode pin die verbonden wordt met +5V (3.3V) voeding

**S:** Een oranje signaalpin die wordt aangestuurd via PWM-signaal

![](media/A144.png)

**Bedieningsprincipe:** De rotatiehoek wordt geregeld via de duty cycle van PWM. Theoretisch is de standaard PWM-cyclus 20ms (50Hz), dus de pulsbreedte moet liggen tussen 1ms en 2ms. In de praktijk varieert de pulsbreedte echter van 0.5ms tot 2.5ms, wat overeenkomt met 0° tot 180°. Let op dat bij hetzelfde signaal de rotatiehoek kan verschillen per servomerk.

**3. Aansluitschema**

![](media/A145.png)

**4. Testcode**

1. Sleep de twee basisblokken en plaats een "variabele" blok ertussen. Stel het variabeltype in op int, de naam op angle, en wijs 0 toe als beginwaarde.

![](media/A146.png)

2. **Servo draait geleidelijk van 0° naar 180°:** 

Voeg een herhaalblok toe en stel het aantal herhalingen in op 180 (180 hoeken). Sleep een "verander variabele" en een "servo" blok en plaats ze in het herhaalblok. Noem de variabele "angle" en selecteer de modus "++". Stel Servo PIN in op IO4 en de graad op de genoemde variabele. Vergeet niet een vertraging van 15ms toe te voegen.

![](media/A147.png)

3. **Servo draait geleidelijk van 180° naar 0°:** Herhaal stap 2, maar stel de variabele modus in op "--".

![](media/A148.png)

**Volledige code:**

![](media/A149.png)

**5. Testresultaat**

Na het aansluiten van de bedrading en het uploaden van de code begint de servo te draaien van 0° naar 180° en vervolgens van 180° naar 0°.

**6. Code-uitleg**

1. Stel de waarden van de Servo in. Servo pin en rotatiehoek kunnen worden geregeld door parameters in dit blok aan te passen.

![](media/A150.png)

2. Lees de huidige hoek van de Servo uit.

![](media/A151.png)