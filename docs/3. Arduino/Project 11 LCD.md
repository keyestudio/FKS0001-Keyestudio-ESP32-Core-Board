### プロジェクト11 LCD

**1. 説明**

Arduino I2C 1602 LCDは、MCU開発ボードが外部センサーやモジュールと接続するための一般的な補助デバイスです。16文字×2行のLCD画面と調整可能な輝度を備えています。このプログラム可能なモジュールは、データの編集、表示、管理に便利です。さらに、文字や数字だけでなく、温度、湿度、圧力などのセンサー値も表示できます。

その使いやすさから、このディスプレイはスマートホーム製品、産業用監視システム、ロボット制御システム、自動車電子システムなど多くの分野で広く応用されています。

**2. 動作原理**

![](media/A44.png)

IIC通信の原理と同じです。基盤となる機能はライブラリにパッケージ化されているため、直接呼び出して使用できます。興味があれば、基盤となる駆動原理をさらに詳しく調べてみてください。

**3. 配線図**

![](media/A45.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 11 LCD
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); // set the LCD address to 0x27 for a 16 chars and 2 line display

void setup()
{
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();		//Turn on the LCD backlight 
    lcd.setCursor(2,0);		//Set the display position 
    lcd.print("Hello,world!");		//LCD displays "Hello, world!"
    lcd.setCursor(2,1);	
    lcd.print("keyestudio!");		//LCD displays "keyestudio!"
}

void loop()
{
}
```

**5. テスト結果**

配線を接続しコードをアップロードした後、LCDの電源を入れると、「Hello, world!」と「keyestudio!」がLCDに表示されます。

![](media/A46.png)

文字が不鮮明な場合は、小さなマイナスドライバーでバックライトのポテンショメーターを調整してください（適切な力で調整してください）。必要に応じて外部電源を接続してください。

![](media/A47.png)

![](media/A48.png)