### Project 33 ESP32 Read Data

**1. Description**

We learned how to control the led light throught ESP32 wifi and display the IP address on the LCD1602. Next, we will use the esp32 board read the sensor data and transmit it to the web page.

**Notes**

1. You need to prepare your a 2.4GHz frequency WIFI, not 5GHz frequency. It can be a mobile hotspot or a router.
2. The ESP32 board consumes more power when connected to the network, so you need to connect an external power supply to this kit. We provide you with a 6XAA Battery Holder (battery not included), which you can connect to the DC port of the ESP32 integrated board.

![](media/B58.png)![](media/B59.png)

3. When using other devices to control this kit, the ESP32 board needs to be connected to the same network as your control device.

4. Remember your wifi network name and password and fill it into the code before uploading it.

```
const char* ssid = "your_SSID"; // Fill in WiFi name, for example,= "KEYES"
const char* password = "your_password"; // Fill in WiFi password, for example,= "123456"
```

**2. Wiring Diagram**

![](media/B60.png)

**3. Upload Code**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi configuration
const char* ssid = "your-SSID";    // your WiFi name
const char* password = "your-PASSWORD";  // your WiFi password

// Create a Web Server
AsyncWebServer server(80);

// DHT11 configuration
xht11 xht(26);                         //set DHT11 sensor pin to IO26
unsigned char dat[] = { 0, 0, 0, 0 };  //Define an array to store temperature and humidity values
int i = 0;

// photoresistor configuration
#define LDRPIN 34  // connect photoresistor to GPIO34(analog input)

void setup() 
{
  lcd.init();  // initialize the lcd
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi connection
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
  // acquire photoresistor value
  int lightValue = analogRead(LDRPIN);  // read photoresistor analog value

  // Generate HTML page
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // add automatic refresh, refresh the page every 5 seconds
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // diaplay temperature and humidity
  html += "<div class='sensor'>";
  html += "<h3>Temperature</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Humidity</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // diaplay photoresistor resistance value
  html += "<div class='sensor'>";
  html += "<h3>Luminance</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // Update temperature, humidity and light intensity every 2 seconds
  if (!xht.receive(dat)) {
    Serial.println("sensor error");
  }
  delay(2000);
}
```

**4. Test Result**

After uploading the code, LCD1602 shows the IP address. Use a computer or mobile phone that is connected to the same network as the ESP32 board, open the browser and enter the IP address, you can see the sensor values on the control page which refresh every 5 seconds.

![](media/B61.png)

