### プロジェクト33 ESP32 データ読み取り

**1. 説明**

ESP32のWiFiを通じてLEDライトを制御し、IPアドレスをLCD1602に表示する方法を学びました。次に、ESP32ボードを使ってセンサーのデータを読み取り、それをウェブページに送信します。

**注意事項**

1. 2.4GHz帯のWiFiが必要です。5GHz帯は使用できません。モバイルホットスポットやルーターでも構いません。
2. ESP32ボードはネットワーク接続時に消費電力が増えるため、外部電源の接続が必要です。本キットには6本用の単三電池ホルダー（電池は含まれていません）を用意しており、ESP32統合ボードのDCポートに接続できます。

![](media/B58.png)![](media/B59.png)

3. 他のデバイスで本キットを制御する場合、ESP32ボードは制御デバイスと同じネットワークに接続されている必要があります。

4. WiFiのネットワーク名とパスワードを覚えておき、アップロード前にコードに入力してください。

```
const char* ssid = "your_SSID"; // WiFi名を入力、例: "KEYES"
const char* password = "your_password"; // WiFiパスワードを入力、例: "123456"
```

**2. 配線図**

![](media/B60.png)

**3. コードのアップロード**

```
#include <WiFi.h>
#include <ESPAsyncWebServer.h>
#include <xht11.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27, 16, 2);

// WiFi設定
const char* ssid = "your-SSID";    // WiFi名
const char* password = "your-PASSWORD";  // WiFiパスワード

// Webサーバー作成
AsyncWebServer server(80);

// DHT11設定
xht11 xht(26);                         // DHT11センサーをIO26に設定
unsigned char dat[] = { 0, 0, 0, 0 };  // 温度と湿度の値を格納する配列
int i = 0;

// フォトレジスタ設定
#define LDRPIN 34  // フォトレジスタをGPIO34（アナログ入力）に接続

void setup() 
{
  lcd.init();  // LCD初期化
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("IP:");

  // WiFi接続
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

  // クライアントリクエスト処理とページ返却
  server.on("/", HTTP_GET, [](AsyncWebServerRequest* request) {
    String html = generateHTML();
    request->send(200, "text/html", html);
  });

  // Webサーバー開始
  server.begin();
}

String generateHTML() 
{
  // フォトレジスタ値取得
  int lightValue = analogRead(LDRPIN);  // フォトレジスタのアナログ値を読み取り

  // HTMLページ生成
  String html = "<html><head><style>";
  html += "body { font-family: Arial, sans-serif; background-color: #f4f4f4; }";
  html += "h2 { color: #333; }";
  html += "div.sensor { background-color: #fff; padding: 20px; margin: 15px; border-radius: 10px; box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1); }";
  html += "div.sensor h3 { margin: 0; }";
  html += "div.sensor p { font-size: 20px; color: #555; }";
  html += "</style>";
  // 自動更新設定、5秒ごとにページをリフレッシュ
  html += "<meta http-equiv='refresh' content='5'>";
  html += "</head><body>";

  // 温度と湿度の表示
  html += "<div class='sensor'>";
  html += "<h3>Temperature</h3>";
  html += "<p>" + String(dat[2]) + " &deg;C</p>";
  html += "</div>";

  html += "<div class='sensor'>";
  html += "<h3>Humidity</h3>";
  html += "<p>" + String(dat[0]) + " %</p>";
  html += "</div>";

  // フォトレジスタの明るさ値表示
  html += "<div class='sensor'>";
  html += "<h3>Luminance</h3>";
  html += "<p>" + String(lightValue) + "</p>";
  html += "</div>";
  html += "</body></html>";

  return html;
}

void loop() 
{
  // 2秒ごとに温度、湿度、光強度を更新
  if (!xht.receive(dat)) {
    Serial.println("sensor error");
  }
  delay(2000);
}
```

**4. テスト結果**

コードをアップロードすると、LCD1602にIPアドレスが表示されます。ESP32ボードと同じネットワークに接続されたパソコンやスマートフォンでブラウザを開き、IPアドレスを入力すると、5秒ごとに更新される制御ページでセンサーの値を確認できます。

![](media/B61.png)