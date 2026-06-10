### プロジェクト29 IRリモコン制御

**1. 説明**

IRリモコンはIR信号を使ってLEDを制御します。これにより、LEDの制御が大幅に簡素化されます。

**2. 動作原理**

![](media/B41.png)

本プロジェクトでは、約38Kのキャリア周波数を変調に使用することが多いです。

IRリモコンシステムは変調、送信、受信を含みます。変調を通じてデータを送信することで、伝送効率が向上し、消費電力が削減されます。

一般的に、キャリア変調の周波数は30kHz～60kHzの範囲内（通常は38kHz）です。矩形波のデューティ比は1/3で、下図のように送信側の455kHz水晶発振器によって決定されます。

この端の水晶発振器には整数分周が必須で、周波数係数は通常12と評価されます。したがって、455kHz÷12 ≈ 37.9kHz ≈ 38kHzとなります。

**38kHzキャリア（完全）送信図：**

![](media/B42.jpg)

**キャリア周波数:** 38kHz

**波長:** 940nm

**受信角度:** 90°

**制御距離:** 6m

**リモコンボタンの回路図：**

![](media/B43.png)

**3. 配線図**

![](media/B44.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 29.1 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

const uint16_t recvPin = 19;  // 赤外線受信ピン
IRrecv irrecv(recvPin);  // 受信クラスのオブジェクトを作成
decode_results results;   // デコード結果クラスのオブジェクトを作成
long ir_rec;

void setup()
{
  Serial.begin(9600); // シリアルポートを初期化し、ボーレートを9600に設定
  irrecv.enableIRIn(); // 受信開始
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value; // 信号を変数ir_recに代入
    if(ir_rec != 0)
    {		// ボタンが押された時にコードの繰り返し実行を防止
        Serial.print(ir_rec, HEX); // 変数ir_recを16進数で表示
        Serial.println();// 改行
    }
    irrecv.resume(); // IRリモコンの受信を再開し、次の値を受信
  }
} 
```

**5. テスト結果**

配線を接続しコードをアップロードした後、シリアルモニターを開きボーレートを9600に設定します。

リモコンのボタンを押すと、16進数の値が表示されます。

![](media/B45.png)

**6. 知識の拡張**

次に、IRリモコンを使ってLEDを制御します。OKボタンを押すとLEDが点灯し、再度押すと消灯します。

**配線図：**

![](media/B46.png)

**コード：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 29.2 IR Remote Control
  http://www.keyestudio.com
*/
#include <Arduino.h>
#include <IRremoteESP8266.h>
#include <IRrecv.h>
#include <IRutils.h>

int led = 25;
int led_val = 0;
const uint16_t recvPin = 19;  // 赤外線受信ピン
IRrecv irrecv(recvPin);       // 受信クラスのオブジェクトを作成
decode_results results;       // デコード結果クラスのオブジェクトを作成
long ir_rec;

void setup() 
{
  Serial.begin(9600);   // シリアルポートを初期化し、ボーレートを9600に設定
  irrecv.enableIRIn();  // 受信開始
  pinMode(led, OUTPUT);
}

void loop() 
{
  if (irrecv.decode(&results)) 
  {
    ir_rec = results.value;      // 信号を変数ir_recに代入
    if (ir_rec != 0) 
    {           // ボタンが押された時にコードの繰り返し実行を防止
      if (ir_rec == 0xFF02FD) // 受信したIR信号がOKボタンのものか判定
      {  
        led_val = !led_val;      // 変数を反転。初期値が0なら反転後は1になる
        digitalWrite(led, led_val);
      }
    }
    irrecv.resume();  // IRリモコンの受信を再開し、次の値を受信
  }
}
```

**テスト結果：**

OKボタンを押すとLEDが点灯し、再度押すと消灯します。