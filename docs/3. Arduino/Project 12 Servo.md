### プロジェクト12 サーボ

**1. 説明**

このサーボは高性能かつ高精度で、最大回転角度は180°です。わずか9gの軽量設計で、さまざまなミニデバイスに最適です。さらに、起動時間が短く、低騒音で安定性が高い特徴があります。

**2. 動作原理**

**角度範囲:** 180°（360°、180°、90°）

**駆動電圧:** 3.3V または 5V

**ピン:** 3本線

![](media/A49.png)

**GND:** グラウンド（茶色）

**VCC:** +5V（3.3V）電源に接続する赤いピン

**S:** PWM信号で制御されるオレンジ色の信号ピン

![](media/A50.png)

**制御原理:** 回転角度はPWMのデューティサイクルで制御されます。理論上、標準PWM周期は20ms（50Hz）で、パルス幅は1ms～2msの範囲に分布します。しかし実際のパルス幅は0.5ms～2.5msで、これが0°～180°に対応します。同じ信号でも、サーボのブランドによって回転角度が異なる場合があるので注意してください。

**3. 配線図**

![](media/A51.png)

USB電源だけでなく、外部電源を追加してください。

![](media/A52.png)

**4. テストコード**

```
int servoPin = 4;//servo PIN

void setup() 
{
  pinMode(servoPin, OUTPUT);//servo pin is set to output
}

void loop() 
{
  for(int i = 0 ; i <= 180 ; i++) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 0° to 180°
  delay(10);//delay 10ms
  }
  for(int i = 180 ; i >= 0 ; i--) 
  {
   servopulse(servoPin, i);//Set the servo to rotate from 180° to 0°
  delay(10);//delay 10ms
  }
}

void servopulse(int pin, int myangle) 
{ //Impulse function
  int pulsewidth = map(myangle, 0, 180, 500, 2500); //Map Angle to pulse width
  for (int i = 0; i < 10; i++) 
  { //Output a few more pulses
    digitalWrite(pin, HIGH);//Set the servo interface level to high
    delayMicroseconds(pulsewidth);//The number of microseconds of delayed pulse width value
    digitalWrite(pin, LOW);//Lower the level of servo interface
  }
}
```

**5. テスト結果**

配線を接続しコードをアップロードすると、サーボは0°から180°まで回転し、その後逆方向に回転を開始します。