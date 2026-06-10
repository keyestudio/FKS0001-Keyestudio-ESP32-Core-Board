### プロジェクト1 LED点滅

**1. 説明**

LED点滅は初心者向けのシンプルなプロジェクトです。ArduinoボードにLEDを取り付け、Arduino IDEでコードをアップロードするだけで完了します。このプロジェクトはArduinoの概念的な枠組みと使用方法の学習を強化します。

**2. 動作原理**

![](media/A16.png)

- **LED:** 上図はLEDの回路図です。一般的に、出力電流が制限されたIOポートではLEDの明るさが低くなることがあるため、回路にはスイッチとしてNPNトランジスタ(Q2)が使用されています。この場合、トランジスタのベース（ピン1）が高レベルのときにLEDが点灯します。逆に、ベースが低レベルのときはLEDが消灯します。

- **トランジスタスイッチ:** その原理を理解するには電子回路の基礎知識が必要です。詳細はご自身で資料を参照してください。簡単に言うと、LEDの点灯・消灯はトランジスタのベースの高低レベルに依存し、それは開発ボードのピンによって決まります。ベース（ピン1）が高レベルのときLEDが点灯し、低レベルのとき消灯します。

**3. 配線図：**

![](media/A17.png)

**4. コードのアップロード**

```
/*
  keyestudio ESP32 Inventor Learning Kit
  Project 1: LED Blinking
  http://www.keyestudio.com
*/
int ledPin = 5; //Define LED to connect with pin IO5
void setup() 
{
  pinMode(ledPin, OUTPUT);//Set the mode to output
}

void loop() 
{
  digitalWrite(ledPin, HIGH); //Output a high level, LED lights up
  delay(1000);//Delay 1000ms 
  digitalWrite(ledPin, LOW); //Output a low level, LED goes off
  delay(1000);
}
```

**5. テスト結果**

コードをアップロードして電源を入れると、LEDが1秒間点灯し、1秒間消灯します。