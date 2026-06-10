### プロジェクト2 ブリージングLED

**1. 説明**

ArduinoのブリージングLEDは、オンボードのプログラム可能なPWMを利用してアナログ波形を出力します。電源を入れると、波形のデューティサイクルを調整することでLEDの明るさを変化させ、最終的にブリージングLEDの効果を実現します。

この方法により、時間経過に伴ってLEDの明るさを変化させることで環境光をシミュレートできます。また、ブリージングLEDはカラフルなミニライトとして、落ち着いた暖かい雰囲気を作り出すことができます。

**2. PWMとは？**

PWMはデジタル手段でアナログ出力を制御するもので、波形のデューティサイクル（高レベルと低レベルを周期的に切り替える信号）を調整できます。

Arduinoの場合、電圧出力のデジタルポートはLOWとHIGHで、それぞれ0Vと5Vに対応します。一般的にLOWを0、HIGHを1と定義します。Arduinoは1秒間に500回の0または1の信号を出力します。信号が「1」の場合は5Vが出力されます。逆にすべて0の場合は0Vが出力されます。あるいは0101010101...のように交互に出力されると、平均出力は2.5Vになります。

つまり、0と1の出力比率が電圧値に影響し、単位時間あたりに出力される0と1の信号が多いほど制御はより正確になります。

ESP32のGPIO34、35、36、39はPWMを使用できません。

![](media/A18.png)

**3. 配線図**

![](media/A19.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 2: Breathing LED
  http://www.keyestudio.com
*/
#define PIN_LED   5   //define the led pin
#define CHN       0   //define the pwm channel
#define FRQ       1000  //define the pwm frequency
#define PWM_BIT   8     //define the pwm precision

void setup() 
{
  ledcSetup(CHN, FRQ, PWM_BIT); //setup pwm channel
  ledcAttachPin(PIN_LED, CHN);  //attach the led pin to pwm channel
}

void loop() 
{
  for (int i = 0; i < 255; i++) //make light fade in
  { 
    ledcWrite(CHN, i);
    delay(10);
  }
  for (int i = 255; i > -1; i--) //make light fade out
  {  
    ledcWrite(CHN, i);
    delay(10);
  }
}
```

**5. テスト結果**

コードをアップロードすると、LEDがゆっくりと明るくなり、暗くなる様子が見られ、まるで呼吸のリズムのようです。