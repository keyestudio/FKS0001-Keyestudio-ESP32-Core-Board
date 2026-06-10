### Project 34 Slimme Huis

**1. Beschrijving**

In dit project simuleren we het slimme huis met de inventor kit.

**Opmerkingen**

1. Je moet een 2.4GHz frequentie WIFI voorbereiden, geen 5GHz frequentie. Dit kan een mobiele hotspot of een router zijn.  
2. De ESP32 board verbruikt meer stroom wanneer verbonden met het netwerk, dus je moet een externe voeding aansluiten op deze kit. We leveren een 6XAA Batterijhouder (batterijen niet inbegrepen), die je kunt aansluiten op de DC-poort van de ESP32 geïntegreerde board.

![](media/B62.png)![](media/B63.png)

3. Wanneer je andere apparaten gebruikt om deze kit te bedienen, moet de ESP32 board verbonden zijn met hetzelfde netwerk als je bedieningsapparaat.

4. Onthoud je wifi-netwerknaam en wachtwoord en vul deze in de code in voordat je deze uploadt.

```
const char* ssid = "your_SSID"; // Vul WiFi naam in, bijvoorbeeld,= "KEYES"
const char* password = "your_password"; // Vul WiFi wachtwoord in, bijvoorbeeld,= "123456"
```

**2. Aansluitschema**

![](media/B64.png)

**3. Code Uploaden**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi configuratie
const char* ssid = "your-SSID";     // jouw WiFi naam
const char* password = "your-PASSWORD";  // jouw WiFi wachtwoord

// DHT11 configuratie
xht11 xht(26);                         // stel DHT11 sensor pin in op IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Definieer een array om temperatuur- en vochtigheidswaarden op te slaan
int i = 0;

// fotoresistor analoge pin
#define LDR_PIN 34  // sluit de fotoresistor aan op GPIO 34

// LED pinnen
#define redLED_PIN 12
#define yellowLED_PIN 13
#define greenLED_PIN 14
#define blueLED_PIN 15
// LED status
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;

// Webserver
AsyncWebServer server(80);

String generateHTML() {
  String html = "<html><head><style>";

  // basisopmaak
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";

  // knopopmaak
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // kleur van LED aan
  html += "button.off { background-color: #f44336; color: white; }";  // kleur van LED uit

  html += "</style>";
  html += "<meta http-equiv='refresh' content='5'>";  // Automatisch verversen elke 5 seconden
  html += "</head><body>";

  // temperatuur
  html += "<h2>Sensor Data</h2>";

  html += "<div class='sensor'>";
  html += "<h3>Temperatuur</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";
  // vochtigheid
  html += "<div class='sensor'>";
  html += "<h3>Vochtigheid</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // toon fotoresistor weerstandwaarde
  int lightValue = analogRead(LDR_PIN);  // fotoresistor waarde
  html += "<div class='sensor'>";
  html += "<h3>Lichtsterkte</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";

  // LED bedieningsknoppen
  html += "<h2>LED's bedienen</h2>";
  html += "<button id='btn0' class='" + String(redLEDState ? "on" : "off") + "' onclick='toggleLed(0)'>Rode LED</button>";
  html += "<button id='btn1' class='" + String(yellowLEDState ? "on" : "off") + "' onclick='toggleLed(1)'>Gele LED</button>";
  html += "<button id='btn2' class='" + String(greenLEDState ? "on" : "off") + "' onclick='toggleLed(2)'>Groene LED</button>";
  html += "<button id='btn3' class='" + String(blueLEDState ? "on" : "off") + "' onclick='toggleLed(3)'>Blauwe LED</button>";

  // JavaScript voor LED aan/uit schakelen
  html += "<script>";
  html += "function toggleLed(led) {";
  html += "  var xhr = new XMLHttpRequest();";
  html += "  xhr.open('GET', '/toggle?led=' + led, true);";
  html += "  xhr.send();";

  html += "  var button = document.getElementById('btn' + led);";
  html += "  if (button.classList.contains('off')) {";
  html += "    button.classList.remove('off');";
  html += "    button.classList.add('on');";
  html += "  } else {";
  html += "    button.classList.remove('on');";
  html += "    button.classList.add('off');";
  html += "  }";
  html += "}";
  html += "</script>";

  html += "</body></html>";

  return html;
}

void setup() 
{
  // Initialiseer seriële poort
  Serial.begin(115200);

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

  // Stel LED pinnen in als output
  pinMode(redLED_PIN, OUTPUT);
  pinMode(yellowLED_PIN, OUTPUT);
  pinMode(greenLED_PIN, OUTPUT);
  pinMode(blueLED_PIN, OUTPUT);

  // Verwerk webverzoeken
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    if (!xht.receive(dat)) {
      Serial.println("sensor fout");
    }
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Bedien de LED's
  server.on("/toggle", HTTP_GET, [](AsyncWebServerRequest* request) {
    String led = request->getParam("led")->value();
    int ledNum = led.toInt();
    if (ledNum == 0) {
      redLEDState = !redLEDState;
      digitalWrite(redLED_PIN, redLEDState ? HIGH : LOW);  //  LED 1
    } else if (ledNum == 1) {
      yellowLEDState = !yellowLEDState;
      digitalWrite(yellowLED_PIN, yellowLEDState ? HIGH : LOW);  //  LED 2
    } else if (ledNum == 2) {
      greenLEDState = !greenLEDState;
      digitalWrite(greenLED_PIN, greenLEDState ? HIGH : LOW);  //  LED 3
    } else if (ledNum == 3) {
      blueLEDState = !blueLEDState;
      digitalWrite(blueLED_PIN, blueLEDState ? HIGH : LOW);  //  LED 4
    }
    request->redirect("/");  // Ga terug naar de startpagina
  });

  // Start de webserver
  server.begin();
}

void loop() 
{
  // Lees de temperatuur- en vochtigheidswaarden en werk de webpagina bij
  if (!xht.receive(dat)) 
  {
    Serial.println("sensor fout");
  }
    delay(2000);  // Vernieuw de pagina elke 2 seconden
}
```

**4. Testresultaat**

Na het uploaden van de code toont de LCD1602 het IP-adres. Open de browser, voer het IP-adres in en je ziet de bedieningspagina.

Op dit moment kun je met het bedieningsapparaat de door de sensor uitgelezen waarde lezen en ook de LED aan- en uitzetten.

![](media/B65.jpg)