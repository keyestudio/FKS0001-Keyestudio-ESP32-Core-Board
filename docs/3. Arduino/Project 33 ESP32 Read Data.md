### Projekt 33 ESP32 Daten auslesen

**1. Beschreibung**

Wir haben gelernt, wie man die LED über ESP32 WiFi steuert und die IP-Adresse auf dem LCD1602 anzeigt. Als Nächstes werden wir das ESP32-Board verwenden, um Sensordaten auszulesen und diese an eine Webseite zu übertragen.

**Hinweise**

1. Sie müssen ein 2,4-GHz-WLAN vorbereiten, kein 5-GHz-Netzwerk. Es kann ein mobiler Hotspot oder ein Router sein.  
2. Das ESP32-Board verbraucht mehr Strom, wenn es mit dem Netzwerk verbunden ist, daher müssen Sie eine externe Stromversorgung an dieses Kit anschließen. Wir stellen Ihnen einen 6XAA Batteriehalter (Batterien nicht enthalten) zur Verfügung, den Sie an den DC-Anschluss des integrierten ESP32-Boards anschließen können.

![](media/B58.png)![](media/B59.png)

3. Wenn Sie andere Geräte zur Steuerung dieses Kits verwenden, muss das ESP32-Board mit demselben Netzwerk verbunden sein wie Ihr Steuergerät.

4. Merken Sie sich Ihren WLAN-Netzwerknamen und das Passwort und tragen Sie diese vor dem Hochladen in den Code ein.

```
const char* ssid = "your_SSID"; // WLAN-Name eintragen, z.B. "KEYES"
const char* password = "your_password"; // WLAN-Passwort eintragen, z.B. "123456"
```

**2. Schaltplan**

![](media/B60.png)

**3. Code hochladen**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi-Konfiguration
const char* ssid = "your-SSID";    // Ihr WLAN-Name
const char* password = "your-PASSWORD";  // Ihr WLAN-Passwort

// Webserver erstellen
AsyncWebServer server(80);

// DHT11-Konfiguration
xht11 xht(26);                         // DHT11 Sensor an IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Array zur Speicherung von Temperatur- und Feuchtigkeitswerten
int i = 0;

// Fotowiderstand-Konfiguration
#define LDRPIN 34  // Fotowiderstand an GPIO34 (analog Eingang) anschließen

void setup() 
{
  lcd.init();  // LCD initialisieren
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WLAN-Verbindung
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

  // Client-Anfrage verarbeiten und Seite zurückgeben
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Webserver starten
  server.begin();
}

String generateHTML() 
{
  // Fotowiderstandswert auslesen
  int lightValue = analogRead(LDRPIN);  // Fotowiderstand analog auslesen

  // HTML-Seite generieren
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // automatische Aktualisierung, Seite alle 5 Sekunden neu laden
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // Temperatur und Luftfeuchtigkeit anzeigen
  html += "<div class='sensor'>";
  html += "<h3>Temperatur</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Luftfeuchtigkeit</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // Fotowiderstandswert anzeigen
  html += "<div class='sensor'>";
  html += "<h3>Beleuchtungsstärke</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Temperatur, Luftfeuchtigkeit und Lichtintensität alle 2 Sekunden aktualisieren
  if (!xht.receive(dat)) {
    Serial.println("sensor error");
  }
  delay(2000);
}
```

**4. Testergebnis**

Nach dem Hochladen des Codes zeigt das LCD1602 die IP-Adresse an. Verwenden Sie einen Computer oder ein Mobiltelefon, das mit demselben Netzwerk wie das ESP32-Board verbunden ist, öffnen Sie den Browser und geben Sie die IP-Adresse ein. Sie sehen die Sensorwerte auf der Steuerungsseite, die alle 5 Sekunden aktualisiert wird.

![](media/B61.png)