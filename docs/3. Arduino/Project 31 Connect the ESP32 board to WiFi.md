### Projekt 31 ESP32-Board mit WiFi verbinden

**1. Beschreibung**

Der ESP32 verfügt über ein integriertes Wi-Fi- und Bluetooth-Modul, das häufig im Internet der Dinge (IoT) eingesetzt wird. Mit dieser Funktion kann er die Datenübertragung über das drahtlose Netzwerk fernsteuern.

In Anwendungen kann der ESP32 als Client verwendet werden, um sich mit einem Wi-Fi-Netzwerk zu verbinden, oder als Hotspot, um ein eigenes Netzwerk zu erstellen. Über diese Verbindungen empfängt der ESP32 Befehle zur Steuerung externer Geräte, wie z.B. das Ein- und Ausschalten von Lichtern oder die Temperaturregelung. Im Code werden Protokolle wie HTTP und MQTT verwendet, um mit dem Server zu kommunizieren und so das Senden und Empfangen von Daten zu ermöglichen, um eine Fernsteuerung und Überwachung zu realisieren.

**2. ESP32 WiFi**

Das ESP32-Entwicklungsboard verfügt über integriertes Wi-Fi (2,4 GHz) und Bluetooth (4.2), die es ermöglichen, sich einfach mit einem Wi-Fi-Netzwerk zu verbinden und mit anderen Geräten im Netzwerk zu kommunizieren. Sie können über den ESP32 Webseiten in Ihrem Browser anzeigen lassen.

· Basisstationsmodus (STA / Wi-Fi Client-Modus): ESP32 ist mit einem Wi-Fi-Hotspot (AP) verbunden.

· AP-Modus (Soft-AP / Wi-Fi-Hotspot-Modus): Wi-Fi-Gerät(e) sind mit dem ESP32 verbunden.

· AP-STA-Modus: ESP32 ist sowohl Wi-Fi-Hotspot als auch Wi-Fi-Gerät, das mit einem anderen Wi-Fi verbunden ist.

· Diese Modi unterstützen mehrere Sicherheitsmodi, einschließlich WPA, WPA2 und WEP.

· Es kann Wi-Fi-Hotspots scannen (aktiv oder passiv).

· Es unterstützt den Promiscuous-Modus zur Überwachung von IEEE802.11 Wi-Fi-Paketen.

**3. Schaltplan**

![](media/B50.png)

**Hinweise:**

1. Sie müssen ein 2,4-GHz-WLAN vorbereiten (kein 5-GHz). Es kann ein mobiler Hotspot oder ein Router sein.

2. Das ESP32-Board verbraucht mehr Strom, wenn es mit dem Netzwerk verbunden ist, daher müssen Sie eine externe Stromversorgung an dieses Kit anschließen. Wir stellen Ihnen einen 6XAA-Batteriehalter (Batterien nicht enthalten) zur Verfügung, den Sie an den DC-Anschluss des integrierten ESP32-Boards anschließen können.

   ![](media/B51.jpg)

3. Merken Sie sich Ihren WLAN-Netzwerknamen und das Passwort und tragen Sie diese vor dem Hochladen in den Code ein.

```
const char* ssid = "your_SSID"; // WLAN-Name eintragen, z.B. "KEYES"
const char* password = "your_password"; // WLAN-Passwort eintragen, z.B. "123456"
```

**4. Code hochladen**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 31 ESP32 WiFi
  http://www.keyestudio.com
*/
#include <WiFi.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
const char* ssid = "your_SSID"; // WLAN-Name einstellen
const char* password = "your_password"; // WLAN-Passwort einstellen
WiFiServer server(80);
int i = 0;

void setup() 
{
  lcd.init();  // LCD initialisieren
  // Wir beginnen mit der Verbindung zu einem WiFi-Netzwerk
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

**5. Testergebnis**

Nach dem Hochladen des Codes zeigt das LCD1602 die IP-Adresse des WiFi an, mit dem der ESP32 verbunden ist.

![](media/B52.png)

**6. Wissensvertiefung**

Die IP-Adresse zeigt „Hello World!“.

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi-Konfiguration

const char* ssid = "your-SSID";     // Ihr WLAN-Name
const char* password = "your-PASSWORD";  // Ihr WLAN-Passwort
int i = 0;
// Webserver erstellen
AsyncWebServer server(80);

void setup() 
{
  lcd.init();  // LCD initialisieren
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi-Verbindung
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
  // HTML-Seite generieren
  String html = "<html><head>";
  html += "<h1>Hello, World!</h1>";
  html += "</head></html>";
  return html;
}

void loop() 
{
}
```

**7. Testergebnis**

Verwenden Sie einen Computer oder ein Mobiltelefon, das mit demselben Netzwerk wie das ESP32-Board verbunden ist, und rufen Sie die auf dem LCD1602 angezeigte IP-Adresse auf. Sie sehen „Hello world“.

![](media/B53.png)