### プロジェクト19 調光ランプ

**1. 説明**

調光ランプは、ポテンショメーターとArduinoコントローラーを使ってLEDの明るさを調整します。明るさは抵抗値に依存し、ポテンショメーターの端をボードのデジタルまたはアナログピンに接続することで読み取り・調整が可能です。さらに、このシステムはファン、電球、ヒーターなど他のデバイスの電圧や電流の制御にも応用できます。

**2. 動作原理**

![](media/B3.png)

![](media/B4.png)

本質的に、ポテンショメーターは抵抗値を変化させることができる素子です。オームの法則(U=I*R)によれば、抵抗は電圧に影響を与えます。今回のポテンショメーターは10Kです。

このプロジェクトでは、最大抵抗値は10Kです。ESP32ボードは3Vの電圧を4095分割（3/4095=0.0007326007326）します。アナログ電圧は読み取った値に0.0007326007326を掛けることで得られます。

**3. 配線図**

![](media/B5.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.1 Dimming Lamp
  http://www.keyestudio.com
*/
int pot = 34;      //Define variable pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);	//Read io34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. テスト結果**

配線を接続しコードをアップロードした後、シリアルモニターを開きボーレートを9600に設定すると、0～4095の範囲でアナログ値が表示されます。ポテンショメーターを回すことでアナログ値の大きさが変化します。

![](media/B6.png)

**6. 知識の拡張**

ポテンショメーターを使ってLEDの明るさを制御します。ご存知のように、これはPWMに影響されます。しかし、アナログ値の範囲は0～4095であるのに対し、PWMの範囲は0～255です。したがって、"map(value, fromLow, fromHigh, toLow, toHigh)"関数が必要になります。

**配線図：**

![](media/B7.png)

**コード：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 19.2 Dimming Lamp
  http://www.keyestudio.com
*/
int led = 25;		//Define LED to IO25
int pot = 34;		//Define pot to IO34

void setup() 
{
  // put your setup code here, to run once:
  pinMode(led,OUTPUT);		//Set LED pin to output 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(pot);
  int led_val = map(value,0,4095,0,255);  //Convert the range of potentiometer analog value to the range we need  
  analogWrite(led,led_val);
}
```

**7. テスト結果**

コードのアップロードが成功した後、ポテンショメーターを回すと赤色LEDの明るさが変化します。