### プロジェクト31 ESP32ボードをWiFiに接続する

**1. 説明**

ESP32は内蔵のWi-FiおよびBluetoothモジュールを搭載しており、IoT（モノのインターネット）で広く使用されています。この機能により、無線ネットワークを通じてデータ送信を遠隔制御できます。

実際の応用では、ESP32はクライアントとしてWi-Fiネットワークに接続したり、ホットスポットとして独自のネットワークを作成したりできます。これらの接続を通じて、ESP32は外部デバイスの制御コマンドを受信し、例えばライトのオン/オフや温度調整を行います。コード内ではHTTPやMQTTなどのプロトコルを使ってサーバーと通信し、データの送受信を行い、遠隔制御や監視を実現します。

**2. ESP32のWiFi機能**

ESP32開発ボードは内蔵のWi-Fi（2.4G）およびBluetooth（4.2）を備えており、Wi-Fiネットワークへの簡単な接続やネットワーク内の他デバイスとの通信が可能です。ESP32を介してブラウザにウェブページを表示できます。

· ベースステーションモード（STA / Wi-Fiクライアントモード）：ESP32がWi-Fiホットスポット（AP）に接続されます。

· APモード（Soft-AP / Wi-Fiホットスポットモード）：Wi-FiデバイスがESP32に接続されます。

· AP-STAモード：ESP32がWi-Fiホットスポットであると同時に、別のWi-Fiに接続されるデバイスでもあります。

· これらのモードはWPA、WPA2、WEPなど複数のセキュリティモードをサポートします。

· Wi-Fiホットスポットのスキャン（アクティブまたはパッシブ）が可能です。

· IEEE802.11 Wi-Fiパケットのプロミスキャスモード監視をサポートします。

**3. 配線図**

![](media/B50.png)

**注意事項:**

1. 2.4GHz帯のWiFi（5GHzではない）を用意してください。モバイルホットスポットやルーターでも構いません。

2. ESP32ボードはネットワーク接続時に消費電力が増えるため、外部電源を接続する必要があります。6本の単三電池ホルダー（電池は含まれていません）を用意しており、ESP32統合ボードのDCポートに接続できます。

   ![](media/B51.jpg)

3. WiFiのネットワーク名とパスワードを覚えておき、コードにアップロード前に入力してください。

```
const char* ssid = "your_SSID"; // WiFi名を入力、例："KEYES"
const char* password = "your_password"; // WiFiパスワードを入力、例："123456"
```

**4. コードのアップロード**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 31 ESP32 WiFi
  http://www.keyestudio.com
*/
#include <WiFi.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2);
const char* ssid = "your_SSID"; // WiFi名を設定
const char* password = "your_password"; // WiFiパスワードを設定
WiFiServer server(80);
int i = 0;

void setup() 
{
  lcd.init();  // LCDを初期化
  // WiFiネットワークへの接続を開始
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

**5. テスト結果**

コードをアップロードすると、LCD1602にESP32が接続したWiFiのIPアドレスが表示されます。

![](media/B52.png)

**6. 知識の拡張**

IPアドレスの表示を「Hello World!」に変更します。

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi設定

const char* ssid = "your-SSID";     // WiFi名
const char* password = "your-PASSWORD";  // WiFiパスワード
int i = 0;
// Webサーバーを作成
AsyncWebServer server(80);

void setup() 
{
  lcd.init();  // LCDを初期化
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi接続
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

  // クライアントのリクエストを処理しページを返す
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });
  // Webサーバーを開始
  server.begin();
}

String generateHTML()
{
  // HTMLページを生成
  String html = "<html><head>";
  html += "<h1>Hello, World!</h1>";
  html += "</head></html>";
  return html;
}

void loop() 
{
}
```

**7. テスト結果**

ESP32ボードと同じネットワークに接続されたパソコンやスマートフォンで、LCD1602に表示されたIPアドレスにアクセスすると、「Hello world」が表示されます。

![](media/B53.png)