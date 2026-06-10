### Progetto 33 ESP32 Lettura Dati

**1. Descrizione**

Abbiamo imparato come controllare il led tramite ESP32 wifi e visualizzare l'indirizzo IP sul LCD1602. Successivamente, utilizzeremo la scheda esp32 per leggere i dati del sensore e trasmetterli alla pagina web.

**Note**

1. È necessario preparare una rete WIFI a frequenza 2.4GHz, non a 5GHz. Può essere un hotspot mobile o un router.
2. La scheda ESP32 consuma più energia quando è connessa alla rete, quindi è necessario collegare un'alimentazione esterna a questo kit. Forniamo un supporto per 6 batterie AA (batterie non incluse), che può essere collegato alla porta DC della scheda integrata ESP32.

![](media/B58.png)![](media/B59.png)

3. Quando si utilizzano altri dispositivi per controllare questo kit, la scheda ESP32 deve essere connessa alla stessa rete del dispositivo di controllo.

4. Ricordati il nome e la password della tua rete wifi e inseriscili nel codice prima di caricarlo.

```
const char* ssid = "your_SSID"; // Inserisci il nome WiFi, ad esempio,= "KEYES"
const char* password = "your_password"; // Inserisci la password WiFi, ad esempio,= "123456"
```

**2. Schema di Collegamento**

![](media/B60.png)

**3. Caricamento Codice**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configurazione WiFi
const char* ssid = "your-SSID";    // nome WiFi
const char* password = "your-PASSWORD";  // password WiFi

// Creazione Web Server
AsyncWebServer server(80);

// Configurazione DHT11
xht11 xht(26);                         // imposta il pin del sensore DHT11 su IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Definisce un array per memorizzare temperatura e umidità
int i = 0;

// Configurazione fotoresistore
#define LDRPIN 34  // collega il fotoresistore a GPIO34 (ingresso analogico)

void setup() 
{
  lcd.init();  // inizializza il lcd
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

  // Gestione richiesta client e risposta alla pagina
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Avvio del Web server
  server.begin();
}

String generateHTML() 
{
  // acquisizione valore fotoresistore
  int lightValue = analogRead(LDRPIN);  // legge il valore analogico del fotoresistore

  // Genera pagina HTML
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // aggiunge aggiornamento automatico, aggiorna la pagina ogni 5 secondi
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // visualizza temperatura e umidità
  html += "<div class='sensor'>";
  html += "<h3>Temperatura</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Umidità</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // visualizza valore di resistenza del fotoresistore
  html += "<div class='sensor'>";
  html += "<h3>Luminosità</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Aggiorna temperatura, umidità e intensità luminosa ogni 2 secondi
  if (!xht.receive(dat)) {
    Serial.println("errore sensore");
  }
  delay(2000);
}
```

**4. Risultato del Test**

Dopo aver caricato il codice, LCD1602 mostra l'indirizzo IP. Usa un computer o un telefono collegato alla stessa rete della scheda ESP32, apri il browser e inserisci l'indirizzo IP, potrai vedere i valori del sensore sulla pagina di controllo che si aggiorna ogni 5 secondi.

![](media/B61.png)