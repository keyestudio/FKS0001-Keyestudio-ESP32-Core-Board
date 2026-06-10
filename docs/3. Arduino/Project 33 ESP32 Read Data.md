### Project 33 ESP32 Gegevens Lezen

**1. Beschrijving**

We hebben geleerd hoe we de led-licht kunnen aansturen via ESP32 wifi en het IP-adres op de LCD1602 kunnen weergeven. Vervolgens zullen we het esp32 board gebruiken om sensorgegevens te lezen en deze naar een webpagina te verzenden.

**Opmerkingen**

1. Je moet een 2.4GHz frequentie WIFI voorbereiden, geen 5GHz frequentie. Dit kan een mobiele hotspot of een router zijn.  
2. Het ESP32 board verbruikt meer stroom wanneer het verbonden is met het netwerk, dus je moet een externe voeding aansluiten op deze kit. We leveren een 6XAA Batterijhouder (batterijen niet inbegrepen), die je kunt aansluiten op de DC-poort van het ESP32 geïntegreerde board.

![](media/B58.png)![](media/B59.png)

3. Wanneer je andere apparaten gebruikt om deze kit te bedienen, moet het ESP32 board verbonden zijn met hetzelfde netwerk als je bedieningsapparaat.

4. Onthoud je wifi-netwerknaam en wachtwoord en vul deze in de code in voordat je deze uploadt.

```
const char* ssid = "your_SSID"; // Vul WiFi naam in, bijvoorbeeld,= "KEYES"
const char* password = "your_password"; // Vul WiFi wachtwoord in, bijvoorbeeld,= "123456"
```

**2. Aansluitschema**

![](media/B60.png)

**3. Code Uploaden**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi configuratie
const char* ssid = "your-SSID";    // jouw WiFi naam
const char* password = "your-PASSWORD";  // jouw WiFi wachtwoord

// Maak een Web Server aan
AsyncWebServer server(80);

// DHT11 configuratie
xht11 xht(26);                         // stel DHT11 sensor pin in op IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Definieer een array om temperatuur- en vochtigheidswaarden op te slaan
int i = 0;

// fotoresistor configuratie
#define LDRPIN 34  // sluit fotoresistor aan op GPIO34 (analoge ingang)

void setup() 
{
  lcd.init();  // initialiseer de lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi verbinding
  WiFi.begin(ssid, password);
  while (WiFi.status() != WL_CONNECTED) {
    lcd.setCursor(i, 1);
    lcd.print(".");
    delay(500);
    i++;
    if (i > 15) {
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
  // verkrijg fotoresistor waarde
  int lightValue = analogRead(LDRPIN);  // lees fotoresistor analoge waarde

  // Genereer HTML pagina
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // voeg automatische verversing toe, vernieuw de pagina elke 5 seconden
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // toon temperatuur en vochtigheid
  html += "<div class='sensor'>";
  html += "<h3>Temperatuur</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Vochtigheid</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // toon fotoresistor weerstandwaarde
  html += "<div class='sensor'>";
  html += "<h3>Lichtintensiteit</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Werk temperatuur, vochtigheid en lichtintensiteit elke 2 seconden bij
  if (!xht.receive(dat)) {
    Serial.println("sensor error");
  }
  delay(2000);
}
```

**4. Testresultaat**

Na het uploaden van de code toont de LCD1602 het IP-adres. Gebruik een computer of mobiele telefoon die verbonden is met hetzelfde netwerk als het ESP32 board, open de browser en voer het IP-adres in. Je ziet de sensorwaarden op de bedieningspagina die elke 5 seconden wordt vernieuwd.

![](media/B61.png)