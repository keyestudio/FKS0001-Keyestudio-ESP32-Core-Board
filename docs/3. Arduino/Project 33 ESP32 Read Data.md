### Proyecto 33 ESP32 Leer Datos

**1. Descripción**

Aprendimos cómo controlar la luz led a través del WiFi del ESP32 y mostrar la dirección IP en el LCD1602. A continuación, usaremos la placa ESP32 para leer los datos del sensor y transmitirlos a la página web.

**Notas**

1. Necesitas preparar un WIFI de frecuencia 2.4GHz, no de 5GHz. Puede ser un hotspot móvil o un router.
2. La placa ESP32 consume más energía cuando está conectada a la red, por lo que necesitas conectar una fuente de alimentación externa a este kit. Te proporcionamos un portapilas de 6XAA (pilas no incluidas), que puedes conectar al puerto DC de la placa integrada ESP32.

![](media/B58.png)![](media/B59.png)

3. Al usar otros dispositivos para controlar este kit, la placa ESP32 debe estar conectada a la misma red que tu dispositivo de control.

4. Recuerda el nombre y la contraseña de tu red wifi y complétalos en el código antes de subirlo.

```
const char* ssid = "your_SSID"; // Completa con el nombre del WiFi, por ejemplo,= "KEYES"
const char* password = "your_password"; // Completa con la contraseña del WiFi, por ejemplo,= "123456"
```

**2. Diagrama de Conexiones**

![](media/B60.png)

**3. Subir Código**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Configuración WiFi
const char* ssid = "your-SSID";    // nombre de tu WiFi
const char* password = "your-PASSWORD";  // contraseña de tu WiFi

// Crear un servidor web
AsyncWebServer server(80);

// Configuración DHT11
xht11 xht(26);                         // asignar pin del sensor DHT11 a IO26
unsigned char dat[] = { 0, 0, 0, 0 };  // Definir un arreglo para almacenar valores de temperatura y humedad
int i = 0;

// Configuración fotoresistor
#define LDRPIN 34  // conectar fotoresistor a GPIO34 (entrada analógica)

void setup() 
{
  lcd.init();  // inicializar el lcd
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

  // Procesar la solicitud del cliente y devolver la página
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Iniciar el servidor web
  server.begin();
}

String generateHTML() 
{
  // obtener valor del fotoresistor
  int lightValue = analogRead(LDRPIN);  // leer valor analógico del fotoresistor

  // Generar página HTML
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // agregar actualización automática, refrescar la página cada 5 segundos
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // mostrar temperatura y humedad
  html += "<div class='sensor'>";
  html += "<h3>Temperatura</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Humedad</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // mostrar valor de resistencia del fotoresistor
  html += "<div class='sensor'>";
  html += "<h3>Luminancia</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Actualizar temperatura, humedad e intensidad de luz cada 2 segundos
  if (!xht.receive(dat)) {
    Serial.println("error del sensor");
  }
  delay(2000);
}
```

**4. Resultado de la Prueba**

Después de subir el código, el LCD1602 muestra la dirección IP. Usa una computadora o teléfono móvil conectado a la misma red que la placa ESP32, abre el navegador e ingresa la dirección IP, podrás ver los valores del sensor en la página de control que se actualiza cada 5 segundos.

![](media/B61.png)