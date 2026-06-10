### Projekt 32 ESP32 WiFi Steuerung LED

**1. Beschreibung**

Als nächstes lernen wir, die LED über WiFi auf einem Mobiltelefon oder Computer zu steuern.

**Hinweise:**

1. Sie müssen ein 2,4-GHz-WLAN vorbereiten, kein 5-GHz-WLAN. Es kann ein mobiler Hotspot oder ein Router sein.

2. Das ESP32-Board verbraucht mehr Strom, wenn es mit dem Netzwerk verbunden ist, daher müssen Sie eine externe Stromversorgung an dieses Kit anschließen. Wir stellen Ihnen einen 6XAA Batteriehalter (Batterien nicht enthalten) zur Verfügung, den Sie an den DC-Anschluss des ESP32-Boards anschließen können.

![](media/B54.png)![](media/B55.png)

3. Wenn Sie andere Geräte zur Steuerung dieses Kits verwenden, muss das ESP32-Board mit demselben Netzwerk wie Ihr Steuergerät verbunden sein.

4. Merken Sie sich Ihren WLAN-Netzwerknamen und das Passwort und tragen Sie diese vor dem Hochladen in den Code ein.

```
const char* ssid = "your_SSID"; // WLAN-Name eintragen, z.B. "KEYES"
const char* password = "your_password"; // WLAN-Passwort eintragen, z.B. "123456"
```

**2. Schaltplan**

![](media/B56.png)

**3. Code hochladen**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi-Konfiguration
const char* ssid = "your-SSID";    // Ihr WLAN-Name
const char* password = "your-PASSWORD";  // Ihr WLAN-Passwort

// Webserver erstellen
AsyncWebServer server(80);

// LED-Pin-Konfiguration
#define redLED 12
#define yellowLED 13
#define greenLED 14
#define blueLED 15

// LED-Zustand
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;
int i = 0;

// HTML-Seite erstellen
String generateHTML() 
{
  String html = "<html><head><style>";
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // Farbe der eingeschalteten LED
  html += "button.off { background-color: #f44336; color: white; }";  // Farbe der ausgeschalteten LED
  html += "</style></head><body>";

  // Verkettung nach Umwandlung eines konstanten Strings in ein String-Objekt mit String()
  html += "<button id='btn0' class='" + String(redLEDState ? "on" : "off") + "' onclick='toggleLed(0)'>rote LED</button>";
  html += "<button id='btn1' class='" + String(yellowLEDState ? "on" : "off") + "' onclick='toggleLed(1)'>gelbe LED</button>";
  html += "<button id='btn2' class='" + String(greenLEDState ? "on" : "off") + "' onclick='toggleLed(2)'>grüne LED</button>";
  html += "<button id='btn3' class='" + String(blueLEDState ? "on" : "off") + "' onclick='toggleLed(3)'>blaue LED</button>";
    
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
  html += "</script></body></html>";
  return html;
}

void setup() 
{
  // Serielle Schnittstelle initialisieren
  Serial.begin(115200);

  // LED-Pins als Ausgang setzen
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
  digitalWrite(redLED, LOW);  // Anfangs sind alle LEDs aus
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  digitalWrite(blueLED, LOW);

  lcd.init();  // LCD initialisieren
  // Wir starten mit der Verbindung zu einem WiFi-Netzwerk
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi-Verbindung
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

  // Client-Anfragen verarbeiten
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    request->send(200, "text/html", generateHTML());  // Zurück zur HTML-Seite
  });

  // LED-Zustand steuern
  server.on("/toggle", HTTP_GET, [](AsyncWebServerRequest* request) {
    if (request->hasParam("led")) {
      int led = request->getParam("led")->value().toInt();
      if (led == 0) {
        redLEDState = !redLEDState;
        digitalWrite(redLED, redLEDState ? HIGH : LOW);
      } else if (led == 1) {
        yellowLEDState = !yellowLEDState;
        digitalWrite(yellowLED, yellowLEDState ? HIGH : LOW);
      } else if (led == 2) {
        greenLEDState = !greenLEDState;
        digitalWrite(greenLED, greenLEDState ? HIGH : LOW);
      } else if (led == 3) {
        blueLEDState = !blueLEDState;
        digitalWrite(blueLED, blueLEDState ? HIGH : LOW);
      }
    }
    request->send(200, "text/plain", "OK");  // Antwort zurücksenden
  });

  // Webserver starten
  server.begin();
}

void loop() 
{
  // Im loop() muss nichts gemacht werden, alle Prozesse laufen asynchron im Webserver
}
```

**4. Testergebnis**

Nach dem Hochladen des Codes zeigt das LCD1602 die IP-Adresse des WLANs an. Verwenden Sie einen Computer oder ein Mobiltelefon, das mit demselben Netzwerk wie das ESP32-Board verbunden ist, öffnen Sie den Browser und geben Sie die IP-Adresse ein, dann sehen Sie die Steuerungsseite.

![](media/B57.png)