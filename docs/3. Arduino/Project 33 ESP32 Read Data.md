### Projet 33 ESP32 Lecture de Données

**1. Description**

Nous avons appris à contrôler la LED via le WiFi de l'ESP32 et afficher l'adresse IP sur le LCD1602. Ensuite, nous allons utiliser la carte ESP32 pour lire les données du capteur et les transmettre à une page web.

**Notes**

1. Vous devez préparer un réseau WIFI à fréquence 2,4 GHz, pas 5 GHz. Cela peut être un hotspot mobile ou un routeur.
2. La carte ESP32 consomme plus d'énergie lorsqu'elle est connectée au réseau, vous devez donc connecter une alimentation externe à ce kit. Nous vous fournissons un porte-piles 6XAA (piles non incluses), que vous pouvez connecter au port DC de la carte ESP32 intégrée.

![](media/B58.png)![](media/B59.png)

3. Lors de l'utilisation d'autres appareils pour contrôler ce kit, la carte ESP32 doit être connectée au même réseau que votre appareil de contrôle.

4. N'oubliez pas le nom et le mot de passe de votre réseau WiFi et remplissez-les dans le code avant de le téléverser.

```
const char* ssid = "your_SSID"; // Remplir le nom du WiFi, par exemple,= "KEYES"
const char* password = "your_password"; // Remplir le mot de passe WiFi, par exemple,= "123456"
```

**2. Schéma de câblage**

![](media/B60.png)

**3. Téléversement du code**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuration WiFi
const char* ssid = "your-SSID";    // nom de votre WiFi
const char* password = "your-PASSWORD";  // mot de passe de votre WiFi

// Création d'un serveur Web
AsyncWebServer server(80);

// Configuration DHT11
xht11 xht(26);                         // définir la broche du capteur DHT11 sur IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Définir un tableau pour stocker les valeurs de température et d'humidité
int i = 0;

// Configuration photoresistance
#define LDRPIN 34  // connecter la photoresistance à GPIO34 (entrée analogique)

void setup() 
{
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

  // Traiter la requête client et retourner la page
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Démarrer le serveur Web
  server.begin();
}

String generateHTML() 
{
  // acquérir la valeur de la photoresistance
  int lightValue = analogRead(LDRPIN);  // lire la valeur analogique de la photoresistance

  // Générer la page HTML
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // ajout du rafraîchissement automatique, rafraîchir la page toutes les 5 secondes
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // afficher la température et l'humidité
  html += "<div class='sensor'>";
  html += "<h3>Température</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Humidité</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // afficher la valeur de résistance de la photoresistance
  html += "<div class='sensor'>";
  html += "<h3>Luminance</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Mettre à jour la température, l'humidité et l'intensité lumineuse toutes les 2 secondes
  if (!xht.receive(dat)) {
    Serial.println("erreur capteur");
  }
  delay(2000);
}
```

**4. Résultat du test**

Après avoir téléversé le code, le LCD1602 affiche l'adresse IP. Utilisez un ordinateur ou un téléphone mobile connecté au même réseau que la carte ESP32, ouvrez le navigateur et entrez l'adresse IP, vous pouvez voir les valeurs des capteurs sur la page de contrôle qui se rafraîchit toutes les 5 secondes.

![](media/B61.png)