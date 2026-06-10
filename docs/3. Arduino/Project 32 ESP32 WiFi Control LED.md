### Proyecto 32 ESP32 WiFi Control LED

**1. Descripción**

A continuación aprenderemos a controlar el LED a través de wifi desde un teléfono móvil o una computadora.

**Notas:**

1. Necesitas preparar una red WIFI de frecuencia 2.4GHz, no de 5GHz. Puede ser un hotspot móvil o un router.

2. La placa ESP32 consume más energía cuando está conectada a la red, por lo que necesitas conectar una fuente de alimentación externa a este kit. Te proporcionamos un portapilas 6XAA (pilas no incluidas), que puedes conectar al puerto DC de la placa integrada ESP32.

![](media/B54.png)![](media/B55.png)

3. Al usar otros dispositivos para controlar este kit, la placa ESP32 debe estar conectada a la misma red que tu dispositivo de control.

4. Recuerda el nombre y la contraseña de tu red wifi y complétalos en el código antes de subirlo.

```
const char* ssid = "your_SSID"; // Completa con el nombre del WiFi, por ejemplo,= "KEYES"
const char* password = "your_password"; // Completa con la contraseña del WiFi, por ejemplo,= "123456"
```

**2. Diagrama de Conexiones**

![](media/B56.png)

**3. Subir Código**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuración WiFi
const char* ssid = "your-SSID";    // nombre de tu WiFi
const char* password = "your-PASSWORD";  // contraseña de tu WiFi

// Crear un servidor web
AsyncWebServer server(80);

// Configuración de pines LED
#define redLED 12
#define yellowLED 13
#define greenLED 14
#define blueLED 15

// Estado de los LED
bool redLEDState = false;
bool yellowLEDState = false;
bool greenLEDState = false;
bool blueLEDState = false;
int i = 0;

// Crear página HTML
String generateHTML() 
{
  String html = "<html><head><style>";
  html += "button { font-size: 30px; padding: 15px; margin: 10px; border: none; cursor: pointer; width: 200px; height: 100px; }";
  html += "button.on { background-color: #4CAF50; color: white; }";   // color del LED encendido
  html += "button.off { background-color: #f44336; color: white; }";  // color del LED apagado
  html += "</style></head><body>";

  // Concatenación después de convertir un String constante a un objeto String usando String()
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
  // Inicializar puerto serial
  Serial.begin(115200);

  // Configurar pines LED como salida
  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
  pinMode(blueLED, OUTPUT);
  digitalWrite(redLED, LOW);  // Inicialmente, todos los leds están apagados
  digitalWrite(yellowLED, LOW);
  digitalWrite(greenLED, LOW);
  digitalWrite(blueLED, LOW);

  lcd.init();  // inicializar el lcd
  // Comenzamos conectándonos a una red WiFi
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // Conexión WiFi
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

  // Procesar solicitudes del cliente
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    request->send(200, "text/html", generateHTML());  // Volver a la página HTML
  });

  // Controlar estado del LED
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
    request->send(200, "text/plain", "OK");  // Respuesta de vuelta
  });

  // Iniciar el servidor web
  server.begin();
}

void loop() 
{
  // No es necesario hacer nada en loop(), todo el procesamiento lo realiza el servidor web asíncrono
}
```

**4. Resultado de la Prueba**

Después de subir el código, el LCD1602 muestra la dirección IP del wifi. Usa una computadora o teléfono móvil conectado a la misma red que la placa ESP32, abre el navegador e ingresa la dirección IP, verás la página de control.

![](media/B57.png)