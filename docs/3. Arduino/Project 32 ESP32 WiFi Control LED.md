### Projet 32 ESP32 Contrôle WiFi LED

**1. Description**

Nous allons maintenant apprendre à contrôler la LED via le wifi depuis un téléphone mobile ou un ordinateur.

**Notes :**

1. Vous devez préparer un réseau WIFI en fréquence 2,4 GHz, pas en 5 GHz. Cela peut être un hotspot mobile ou un routeur.

2. La carte ESP32 consomme plus d’énergie lorsqu’elle est connectée au réseau, il est donc nécessaire de connecter une alimentation externe à ce kit. Nous vous fournissons un support pour 6 piles AA (piles non incluses), que vous pouvez connecter au port DC de la carte ESP32 intégrée.

![](media/B54.png)![](media/B55.png)

3. Lors de l’utilisation d’autres appareils pour contrôler ce kit, la carte ESP32 doit être connectée au même réseau que votre appareil de contrôle.

4. N’oubliez pas le nom et le mot de passe de votre réseau wifi et remplissez-les dans le code avant de le téléverser.

```
const char* ssid = "your_SSID"; // Remplissez le nom du WiFi, par exemple,= "KEYES"
const char* password = "your_password"; // Remplissez le mot de passe WiFi, par exemple,= "123456"
```

**2. Schéma de câblage**

![](media/B56.png)

**3. Téléversement du code**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuration WiFi
const char* ssid = "your-SSID";    // nom de votre WiFi
const char* password = "your-PASSWORD";  // mot de passe de votre WiFi

// Création d’un serveur Web
AsyncWebServer server(80);

// Configuration des pins LED
#define redLED 12
#define yellowLED 13
#define greenLED 14
#define blueLED 15

// État des LED
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;
int i = 0;

// Création de la page HTML
String generateHTML() 
{
  String html = "<html><head><style>";
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // couleur LED allumée
  html += "button.off { background-color: #f44336; color: white; }";  // couleur LED éteinte
  html += "</style></head><body>";

  // Concaténation après conversion d’une String constante en objet String via String()
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
  // Initialisation du port série
  Serial.begin(115200);

  // Configuration des pins LED en sortie
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
  digitalWrite(redLED, LOW);  // Initialement, toutes les LED sont éteintes
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  digitalWrite(blueLED, LOW);

  lcd.init();  // initialisation de l’écran lcd
  // On commence par se connecter à un réseau WiFi
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

  // Traitement des requêtes clients
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    request->send(200, "text/html", generateHTML());  // Retour à la page HTML
  });

  // Contrôle de l’état des LED
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
    request->send(200, "text/plain", "OK");  // Réponse de retour
  });

  // Démarrage du serveur Web
  server.begin();
}

void loop() 
{
  // Rien à faire dans loop(), tout est géré par le serveur Web asynchrone
}
```

**4. Résultat du test**

Après le téléversement du code, l’écran LCD1602 affiche l’adresse IP du wifi. Utilisez un ordinateur ou un téléphone mobile connecté au même réseau que la carte ESP32, ouvrez un navigateur et entrez l’adresse IP, vous verrez la page de contrôle.

![](media/B57.png)