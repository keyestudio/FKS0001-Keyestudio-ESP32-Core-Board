### Project 31 Verbind de ESP32 board met WiFi

**1. Beschrijving**

De ESP32 beschikt over een ingebouwde Wi-Fi en Bluetooth module die veel wordt gebruikt in het Internet of Things (IoT). Met deze functie kan het de datatransmissie op afstand via het draadloze netwerk regelen.

In toepassingen kan de ESP32 worden gebruikt als client om verbinding te maken met een Wi-Fi netwerk, of als hotspot om een eigen netwerk te creëren. Via deze verbindingen ontvangt de ESP32 commando's om externe apparaten te bedienen, zoals het aan- en uitzetten van lampen en het aanpassen van de temperatuur. In de code worden protocollen zoals HTTP en MQTT gebruikt om met de server te communiceren voor het verzenden en ontvangen van data, zodat op afstand besturing en monitoring mogelijk is.

**2. ESP32 wifi**

De ESP32 ontwikkelboard is uitgerust met ingebouwde Wi-Fi (2.4G) en Bluetooth (4.2), waardoor het eenvoudig verbinding kan maken met een Wi-Fi netwerk en kan communiceren met andere apparaten in het netwerk. Je kunt webpagina's weergeven in je browser via de ESP32.

· Basisstationmodus (STA / Wi-Fi Client modus): ESP32 is verbonden met een Wi-Fi hotspot (AP).

· AP modus (Soft-AP / Wi-Fi hotspot modus): Wi-Fi apparaat(en) zijn verbonden met de ESP32.

· AP-STA modus: ESP32 is zowel Wi-Fi hotspot als een Wi-Fi apparaat verbonden met een ander Wi-Fi netwerk.

· Deze modi ondersteunen meerdere beveiligingsmodi, waaronder WPA, WPA2 en WEP.

· Het kan Wi-Fi hotspots scannen (actief of passief).

· Het ondersteunt promiscuous modus voor het monitoren van IEEE802.11 Wi-Fi pakketten.

**3. Aansluitschema**

![](media/B50.png)

**Notities:**

1. Je moet een 2.4GHz frequentie WIFI voorbereiden (geen 5GHz). Dit kan een mobiele hotspot of een router zijn.

2. De ESP32 board verbruikt meer stroom wanneer het verbonden is met het netwerk, dus je moet een externe voeding aansluiten op deze kit. We leveren een 6XAA batterijhouder (batterijen niet inbegrepen), die je kunt aansluiten op de DC-poort van de ESP32 geïntegreerde board.

   ![](media/B51.jpg)

3. Onthoud je wifi-netwerknaam en wachtwoord en vul deze in de code in voordat je deze uploadt.

```
const char* ssid = "your_SSID"; // Vul WiFi naam in, bijvoorbeeld,= "KEYES"
const char* password = "your_password"; // Vul WiFi wachtwoord in, bijvoorbeeld,= "123456"
```

**4. Code uploaden**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 31 ESP32 WiFi
  http://www.keyestudio.com
*/
#include <WiFi.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
const char* ssid = "your_SSID"; // stel je WiFi naam in
const char* password = "your_password"; // stel je WiFi wachtwoord in
WiFiServer server(80);
int i = 0;

void setup() 
{
  lcd.init();  // initialiseer de lcd
  // We beginnen met verbinden met een WiFi netwerk
  lcd.backlight();

  lcd.setCursor(0, 0);
  lcd.print("IP:");

  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) 
  {
    lcd.setCursor(i, 1);
    lcd.print(".");
    delay(500);
    i++;
    if (i > 15) 
    {
      i = 0;
      lcd.setCursor(0, 1);
      lcd.print("                ");
    }
  }
  lcd.setCursor(0, 1);
  lcd.print("                ");
  lcd.setCursor(0, 1);
  lcd.print(WiFi.localIP());
}

void loop() 
{
}
```

**5. Testresultaat**

Na het uploaden van de code toont de LCD1602 het IP-adres van het wifi-netwerk waarmee de ESP32 verbonden is.

![](media/B52.png)

**6. Kennisuitbreiding**

Het IP-adres toont “Hello World!”.

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi configuratie

const char* ssid = "your-SSID";     // je WiFi naam
const char* password = "your-PASSWORD";  // je WiFi wachtwoord
int i = 0;
// Maak een Web Server aan
AsyncWebServer server(80);

void setup() 
{
  lcd.init();  // initialiseer de lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi verbinding
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) 
  {
    lcd.setCursor(i, 1);
    lcd.print(".");
    delay(500);
    i++;
    if (i > 15) 
    {
      i = 0;
      lcd.setCursor(0, 1);
      lcd.print("                ");
    }
  }
  lcd.setCursor(0, 1);
  lcd.print("                ");
  lcd.setCursor(0, 1);
  lcd.print(WiFi.localIP());

  // Verwerk de client aanvraag en stuur de pagina terug
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });
  // Start de Web server
  server.begin();
}

String generateHTML()
{
  // Genereer HTML pagina
  String html = "<html><head>";
  html += "<h1>Hello, World!</h1>";
  html += "</head></html>";
  return html;
}

void loop() 
{
}
```

**7. Testresultaat**

Gebruik een computer of mobiele telefoon die verbonden is met hetzelfde netwerk als de ESP32 board, en ga naar het IP-adres dat op de LCD1602 wordt weergegeven. Je zult “Hello world” zien.

![](media/B53.png)