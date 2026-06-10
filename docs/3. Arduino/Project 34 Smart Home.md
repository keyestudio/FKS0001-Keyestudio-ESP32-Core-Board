### Projet 34 Maison Intelligente

**1. Description**

Dans ce projet, nous simulons la maison intelligente avec le kit inventeur.

**Notes**

1. Vous devez préparer un WIFI à fréquence 2,4 GHz, pas à fréquence 5 GHz. Cela peut être un hotspot mobile ou un routeur.
2. La carte ESP32 consomme plus d'énergie lorsqu'elle est connectée au réseau, vous devez donc connecter une alimentation externe à ce kit. Nous vous fournissons un support de 6 piles AA (piles non incluses), que vous pouvez connecter au port DC de la carte ESP32 intégrée.

![](media/B62.png)![](media/B63.png)

3. Lors de l'utilisation d'autres appareils pour contrôler ce kit, la carte ESP32 doit être connectée au même réseau que votre appareil de contrôle.

4. N'oubliez pas le nom et le mot de passe de votre réseau wifi et remplissez-les dans le code avant de le téléverser.

```
const char* ssid = "your_SSID"; // Remplissez le nom du WiFi, par exemple,= "KEYES"
const char* password = "your_password"; // Remplissez le mot de passe WiFi, par exemple,= "123456"
```

**2. Schéma de câblage**

![](media/B64.png)

**3. Téléversement du code**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuration WiFi
const char* ssid = "your-SSID";     // nom de votre WiFi
const char* password = "your-PASSWORD";  // mot de passe de votre WiFi

// Configuration DHT11
xht11 xht(26);                         // définir la broche du capteur DHT11 sur IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Définir un tableau pour stocker les valeurs de température et d'humidité
int i = 0;

// broche analogique photoresistance
#define LDR_PIN 34  // connecter la photoresistance à GPIO 34

// broches LED
#define redLED_PIN 12
#define yellowLED_PIN 13
#define greenLED_PIN 14
#define blueLED_PIN 15
// état des LED
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;

// Serveur Web
AsyncWebServer server(80);

String generateHTML() {
  String html = "<html><head><style>";

  // format de base
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";

  // format des boutons
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // couleur LED allumée
  html += "button.off { background-color: #f44336; color: white; }";  // couleur LED éteinte

  html += "</style>";
  html += "<meta http-equiv='refresh' content='5'>";  // Rafraîchissement automatique toutes les 5 secondes
  html += "</head><body>";

  // température
  html += "<h2>Données du capteur</h2>";

  html += "<div class='sensor'>";
  html += "<h3>Température</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";
  // humidité
  html += "<div class='sensor'>";
  html += "<h3>Humidité</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // affichage de la valeur de résistance de la photoresistance
  int lightValue = analogRead(LDR_PIN);  // valeur photoresistance
  html += "<div class='sensor'>";
  html += "<h3>Luminance</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";

  // bouton de contrôle des LED
  html += "<h2>Contrôle des LEDs</h2>";
  html += "<button id='btn0' class='" + String(redLEDState ? "on" : "off") + "' onclick='toggleLed(0)'>LED Rouge</button>";
  html += "<button id='btn1' class='" + String(yellowLEDState ? "on" : "off") + "' onclick='toggleLed(1)'>LED Jaune</button>";
  html += "<button id='btn2' class='" + String(greenLEDState ? "on" : "off") + "' onclick='toggleLed(2)'>LED Verte</button>";
  html += "<button id='btn3' class='" + String(blueLEDState ? "on" : "off") + "' onclick='toggleLed(3)'>LED Bleue</button>";

  // Contrôle JavaScript LED On/Off
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
  // Initialiser le port série
  Serial.begin(115200);

  lcd.init();  // initialiser le lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // Connexion WiFi
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

  // Définir les broches LED en sortie
  pinMode(redLED_PIN, OUTPUT);
  pinMode(yellowLED_PIN, OUTPUT);
  pinMode(greenLED_PIN, OUTPUT);
  pinMode(blueLED_PIN, OUTPUT);

  // Traiter les requêtes Web
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    if (!xht.receive(dat)) {
      Serial.println("erreur capteur");
    }
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Contrôler l'état des LED
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
    request->redirect("/");  // Retour à la page d'accueil
  });

  // Démarrer le serveur Web
  server.begin();
}

void loop() 
{
  // Lire les valeurs de température et d'humidité et mettre à jour la page web
  if (!xht.receive(dat)) 
  {
    Serial.println("erreur capteur");
  }
    delay(2000);  // Rafraîchir la page toutes les 2 secondes
}
```

**4. Résultat du test**

Après avoir téléversé le code, le LCD1602 affiche l'adresse IP. Ouvrez le navigateur, saisissez l'adresse IP et vous verrez la page de contrôle.

À ce moment, vous pouvez utiliser l'appareil de contrôle pour lire la valeur mesurée par le capteur, et vous pouvez également contrôler l'allumage et l'extinction des LED.

![](media/B65.jpg)