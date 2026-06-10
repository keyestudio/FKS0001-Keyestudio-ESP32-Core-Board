### Projet 31 Connecter la carte ESP32 au WiFi

**1. Description**

L'ESP32 dispose d'un module Wi-Fi et Bluetooth intégré, largement utilisé dans l'Internet des Objets (IoT). Grâce à cette fonction, il peut contrôler à distance la transmission des données via le réseau sans fil.

Dans les applications, l'ESP32 peut être utilisé comme client pour se connecter à un réseau Wi-Fi, ou comme point d'accès pour créer son propre réseau. Grâce à ces connexions, l'ESP32 reçoit des commandes pour contrôler des dispositifs externes, comme allumer/éteindre des lumières et ajuster la température. Dans le code, des protocoles comme HTTP et MQTT sont utilisés pour communiquer avec le serveur afin d'envoyer et recevoir des données, permettant ainsi un contrôle et une surveillance à distance.

**2. WiFi ESP32**

La carte de développement ESP32 est équipée d'un Wi-Fi intégré (2.4G) et Bluetooth (4.2), ce qui lui permet de se connecter facilement à un réseau Wi-Fi et de communiquer avec d'autres appareils du réseau. Vous pouvez afficher des pages web dans votre navigateur via l'ESP32.

· Mode station de base (STA / mode client Wi-Fi) : l'ESP32 est connecté à un point d'accès Wi-Fi (AP).

· Mode AP (Soft-AP / mode point d'accès Wi-Fi) : un ou plusieurs appareils Wi-Fi sont connectés à l'ESP32.

· Mode AP-STA : l'ESP32 est à la fois point d'accès Wi-Fi et appareil Wi-Fi connecté à un autre réseau Wi-Fi.

· Ces modes supportent plusieurs modes de sécurité, y compris WPA, WPA2 et WEP.

· Il est capable de scanner les points d'accès Wi-Fi (actifs ou passifs).

· Il supporte le mode promiscuous pour surveiller les paquets Wi-Fi IEEE802.11.

**3. Schéma de câblage**

![](media/B50.png)

**Notes :**

1. Vous devez préparer un réseau WIFI à fréquence 2.4GHz (pas 5GHz). Il peut s'agir d'un hotspot mobile ou d'un routeur.

2. La carte ESP32 consomme plus d'énergie lorsqu'elle est connectée au réseau, il est donc nécessaire de connecter une alimentation externe à ce kit. Nous vous fournissons un support pour 6 piles AA (piles non incluses), que vous pouvez connecter au port DC de la carte ESP32 intégrée.

   ![](media/B51.jpg)

3. N'oubliez pas le nom et le mot de passe de votre réseau wifi et remplissez-les dans le code avant de le téléverser.

```
const char* ssid = "your_SSID"; // Remplissez le nom du WiFi, par exemple,= "KEYES"
const char* password = "your_password"; // Remplissez le mot de passe WiFi, par exemple,= "123456"
```

**4. Téléversement du code**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 31 ESP32 WiFi
  http://www.keyestudio.com
*/
#include <WiFi.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
const char* ssid = "your_SSID"; // set to your WiFi name
const char* password = "your_password"; // set your WiFi password
WiFiServer server(80);
int i = 0;

void setup() 
{
  lcd.init();  // initialize the lcd
  // We start by connecting to a WiFi network
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

**5. Résultat du test**

Après avoir téléversé le code, l'écran LCD1602 affiche l'adresse IP du réseau wifi auquel l'ESP32 est connecté.

![](media/B52.png)

**6. Extension des connaissances**

L'adresse IP affiche “Hello World!”.

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuration WiFi

const char* ssid = "your-SSID";     // votre nom WiFi
const char* password = "your-PASSWORD";  // votre mot de passe WiFi
int i = 0;
// Création d'un serveur Web
AsyncWebServer server(80);

void setup() 
{
  lcd.init();  // initialiser le lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // Connexion WiFi
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
  // Générer la page HTML
  String html = "<html><head>";
  html += "<h1>Hello, World!</h1>";
  html += "</head></html>";
  return html;
}

void loop() 
{
}
```

**7. Résultat du test**

Utilisez un ordinateur ou un téléphone mobile connecté au même réseau que la carte ESP32, et accédez à l'adresse IP affichée sur le LCD1602, vous verrez “Hello world”.

![](media/B53.png)