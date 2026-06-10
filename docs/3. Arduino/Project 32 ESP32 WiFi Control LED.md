### Progetto 32 ESP32 WiFi Controllo LED

**1. Descrizione**

Successivamente impareremo a controllare il LED tramite wifi da un telefono cellulare o un computer.

**Note:**

1. È necessario preparare una rete WIFI a frequenza 2.4GHz, non a 5GHz. Può essere un hotspot mobile o un router.

2. La scheda ESP32 consuma più energia quando è connessa alla rete, quindi è necessario collegare un alimentatore esterno a questo kit. Forniamo un portabatterie 6XAA (batterie non incluse), che puoi collegare alla porta DC della scheda integrata ESP32.

![](media/B54.png)![](media/B55.png)

3. Quando si utilizzano altri dispositivi per controllare questo kit, la scheda ESP32 deve essere connessa alla stessa rete del dispositivo di controllo.

4. Ricorda il nome e la password della tua rete wifi e inseriscili nel codice prima di caricarlo.

```
const char* ssid = "your_SSID"; // Inserisci il nome WiFi, ad esempio,= "KEYES"
const char* password = "your_password"; // Inserisci la password WiFi, ad esempio,= "123456"
```

**2. Schema di Collegamento**

![](media/B56.png)

**3. Caricamento del Codice**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configurazione WiFi
const char* ssid = "your-SSID";    // nome della tua WiFi
const char* password = "your-PASSWORD";  // password della tua WiFi

// Creazione del Web Server
AsyncWebServer server(80);

// Configurazione pin LED
#define redLED 12
#define yellowLED 13
#define greenLED 14
#define blueLED 15

// Stato LED
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;
int i = 0;

// Creazione pagina HTML
String generateHTML() 
{
  String html = "<html><head><style>";
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // colore LED acceso
  html += "button.off { background-color: #f44336; color: white; }";  // colore LED spento
  html += "</style></head><body>";

  // Concatenazione dopo aver convertito una Stringa costante in un oggetto String usando String()
  html += "<button id='btn0' class='" + String(redLEDState ? "on" : "off") + "' onclick='toggleLed(0)'>red LED</button>";
  html += "<button id='btn1' class='" + String(yellowLEDState ? "on" : "off") + "' onclick='toggleLed(1)'>yellow LED</button>";
  html += "<button id='btn2' class='" + String(greenLEDState ? "on" : "off") + "' onclick='toggleLed(2)'>green LED</button>";
  html += "<button id='btn3' class='" + String(blueLEDState ? "on" : "off") + "' onclick='toggleLed(3)'>blue LED</button>";
    
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
  // Inizializza la porta seriale
  Serial.begin(115200);

  // Imposta i pin LED come output
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
  digitalWrite(redLED, LOW);  // Inizialmente tutti i LED sono spenti
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  digitalWrite(blueLED, LOW);

  lcd.init();  // inizializza il lcd
  // Iniziamo con la connessione a una rete WiFi
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // Connessione WiFi
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

  // Gestione richieste client
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    request->send(200, "text/html", generateHTML());  // Torna alla pagina HTML
  });

  // Controllo stato LED
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
    request->send(200, "text/plain", "OK");  // Risposta di ritorno
  });

  // Avvia il Web server
  server.begin();
}

void loop() 
{
  // Non è necessario fare nulla in loop(), tutta l'elaborazione è gestita dal Web server asincrono
}
```

**4. Risultato del Test**

Dopo aver caricato il codice, LCD1602 mostra l'indirizzo IP della wifi. Usa un computer o un telefono cellulare connesso alla stessa rete della scheda ESP32, apri il browser e inserisci l'indirizzo IP, vedrai la pagina di controllo.

![](media/B57.png)