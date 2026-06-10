### プロジェクト4 交通信号機

**1. 説明**

交通信号機モジュールは、歩行者や車両の通行を制御するための装置です。赤、黄、緑の3つのライトがあり、それぞれ異なる指示を示します。

**赤は停止:** 歩行者と車両は進行を停止します。

**黄は注意:** 歩行者と車両は停止の準備をします。すでに走行中の場合は速度を落とすべきです。

**緑は進行:** 歩行者と車両は交通規則を守りながら進み続けます。

このプロジェクトでは、Arduinoを使って交通信号機を制御するコードを書くことができます。例えば、各ライトの点灯時間やそれらの間隔を設定できます。さらに、タイマーを追加してライトの色をスケジュール通りに切り替えることも可能です。

**2. 配線図**

![](media/A21.png)

**3. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 4 Traffic Light
  http://www.keyestudio.com
*/
int greenPin = 27;   //Green LED connects to IO27
int yellowPin = 26; //Yellow LED connects to IO26
int redPin = 25;   //Red LED connects to IO25

void setup() 
{
  //Set all LED interfaces to output mode
  pinMode(greenPin, OUTPUT);
  pinMode(yellowPin, OUTPUT);
  pinMode(redPin, OUTPUT);
}

void loop() 
{
  digitalWrite(greenPin, HIGH); //Light green LED up 
  delay(5000);  //Delay 5s
  digitalWrite(greenPin, LOW); //Turn green LED off 
  for (int i = 1; i <= 3; i++) //Execute for 3 times
  {  
    digitalWrite(yellowPin, HIGH); //Light yellow LED up
    delay(500); //Delay 0.5s
    digitalWrite(yellowPin, LOW); // Turn yellow LED off
    delay(500); //Delay 0.5s
  }
  digitalWrite(redPin, HIGH); //Light red LED up 
  delay(5000);  //Delay 5s 
  digitalWrite(redPin, LOW); //Turn red LED off 

}
```

**4. テスト結果**

コードをアップロードすると、緑のLEDが5秒間点灯し、黄のLEDが3回点滅し、赤のLEDが5秒間点灯する動作が繰り返されます。