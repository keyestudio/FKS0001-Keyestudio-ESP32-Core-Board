### Proyecto 31 Conectar la placa ESP32 a WiFi

**1. Descripción**

ESP32 cuenta con un módulo integrado de Wi-Fi y Bluetooth que se utiliza ampliamente en el Internet de las Cosas (IoT). Con esta función, puede controlar remotamente la transmisión de datos a través de la red inalámbrica.

En las aplicaciones, ESP32 puede usarse como cliente para conectarse a una red Wi-Fi, o como un hotspot para crear su propia red. A través de estas conexiones, ESP32 recibe comandos para controlar dispositivos externos, como encender/apagar luces y ajustar la temperatura. En el código, se utilizan protocolos como HTTP y MQTT para comunicarse con el servidor y lograr el envío y recepción de datos, con el fin de controlar y monitorear remotamente.

**2. WiFi del ESP32**

La placa de desarrollo ESP32 viene con Wi-Fi integrado (2.4G) y Bluetooth (4.2), lo que le permite conectarse fácilmente a una red Wi-Fi y comunicarse con otros dispositivos en la red. Puedes mostrar páginas web en tu navegador a través del ESP32.

· Modo estación base (STA / modo cliente Wi-Fi): ESP32 está conectado a un hotspot Wi-Fi (AP).

· Modo AP (Soft-AP / modo hotspot Wi-Fi): dispositivo(s) Wi-Fi está(n) conectado(s) al ESP32.

· Modo AP-STA: ESP32 es tanto hotspot Wi-Fi como un dispositivo Wi-Fi conectado a otra red Wi-Fi.

· Estos modos soportan múltiples modos de seguridad, incluyendo WPA, WPA2 y WEP.

· Es capaz de escanear hotspots Wi-Fi (activo o pasivo).

· Soporta modo promiscuo para monitorear paquetes Wi-Fi IEEE802.11.

**3. Diagrama de conexión**

![](media/B50.png)

**Notas:**

1. Necesitas preparar un WIFI de frecuencia 2.4GHz (no 5GHz). Puede ser un hotspot móvil o un router.

2. La placa ESP32 consume más energía cuando está conectada a la red, por lo que necesitas conectar una fuente de alimentación externa a este kit. Te proporcionamos un portapilas 6XAA (pilas no incluidas), que puedes conectar al puerto DC de la placa integrada ESP32.

   ![](media/B51.jpg)

3. Recuerda el nombre y la contraseña de tu red wifi y complétalos en el código antes de subirlo.

```
const char* ssid = "your_SSID"; // Completa con el nombre del WiFi, por ejemplo,= "KEYES"
const char* password = "your_password"; // Completa con la contraseña del WiFi, por ejemplo,= "123456"
```

**4. Subir código**

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

**5. Resultado de la prueba**

Después de subir el código, el LCD1602 muestra la dirección IP del wifi al que te conectaste con el ESP32.

![](media/B52.png)

**6. Ampliación de conocimientos**

La dirección IP muestra “Holly World!”.

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi configuration

const char* ssid = "your-SSID";     // your WiFi name
const char* password = "your-PASSWORD";  // your WiFi password
int i = 0;
// Create a Web Server
AsyncWebServer server(80);

void setup() 
{
  lcd.init();  // initialize the lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi connection
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

  // Process the client request and return to the page
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });
  // Start the Web server
  server.begin();
}

String generateHTML()
{
  // Generate HTML page
  String html = "<html><head>";
  html += "<h1>Hello, World!</h1>";
  html += "</head></html>";
  return html;
}

void loop() 
{
}
```

**7. Resultado de la prueba**

Usa una computadora o teléfono móvil que esté conectado a la misma red que la placa ESP32, y accede a la dirección IP mostrada en el LCD1602 y verás “Hello world”.

![](media/B53.png)