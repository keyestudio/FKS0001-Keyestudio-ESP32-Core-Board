### プロジェクト23 スマートカップ

**1. 説明**

本プロジェクトでは、主にArduino開発ボードを採用し、RGBインジケーターで内部液体の温度を表示するプログラム可能なスマートカップを作成します。温度の閾値を設定することで、光の明るさを制御できます。閾値を超えると明るくなり、それ以外は暗くなります。

スマートカップは、ユーザーが飲料水の温度をより適切に管理し、過熱や凍結を効果的に防止するのに役立ちます。

**2. 動作原理**

![](media/B23.png)

**3. 配線図**

![](media/B24.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 23.1 Smart Cup
  http://www.keyestudio.com
*/
#include <xht11.h>
xht11 xht(26);   //The DHT11 sensor connects to IO26
unsigned char dat[] = {0,0,0,0}; //Define an array to store temperature and humidity data

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);
}

void loop() 
{
  // put your main code here, to run repeatedly:
  if (xht.receive(dat)) { //Check correct return to true
    Serial.print("RH:");
    Serial.print(dat[0]); //The integral part of humidity,dht[1] is the decimal part
    Serial.print("%  ");
    Serial.print("Temp:");
    Serial.print(dat[2]); //The integer part of the temperature,dht[3] is the decimal part
    Serial.println("C");
  } 
  else 
  {    //Read error
    Serial.println("sensor error");
  }
  delay(1500);  //Delay 1500ms 
}
```

**5. テスト結果**

配線を接続しコードをアップロードした後、シリアルモニターを開きボーレートを9600に設定すると、温度と湿度の値が表示されます。

![](media/B25.png)

**6. 知識の拡張**

ここでは、液体の温度を表示できるスマートカップを作ります。100を4つの範囲に分けてLEDで示します。以下のように設定します：

- **赤色LED:** 100-75°C
- **黄色LED:** 75-50°C
- **緑色LED:** 50-25°C
- **青色LED:** 25-0°C

**配線図：**

![](media/B26.png)

**コード：**

```
/*
  keyestudio ESP32 ESP32 Inventor Learning Kit 
  Project 23.2 Smart Cup
  http://www.keyestudio.com
*/
#include <xht11.h>
xht11 xht(26);                         //Define DHT11 to pin IO26
unsigned char dat[4] = { 0, 0, 0, 0 };  //Define an array to store temperature and humidity data

int red_led = 12;
int yellow_led = 13;   //Define yellow_led to io13
int green_led = 14;    //Define green_led to io14
int blue_led = 27;     //Define blue_led to io27
int temperature = 0;  //Set an variable to save the temperature value

void setup() 
{
  // put your setup code here, to run once:
  pinMode(red_led, OUTPUT);     //Set io12 to ouput 
  pinMode(green_led, OUTPUT);   //Set io13 to ouput 
  pinMode(blue_led, OUTPUT);    //Set io14 to ouput 
  pinMode(yellow_led, OUTPUT);  //Set io27 to ouput 
  Serial.begin(9600);
}

void loop() 
{
  // put your main code here, to run repeatedly:
  if (xht.receive(dat))  //Check correct return to true
  { 
    temperature = dat[2];
    if (temperature > 75) // Determine whether value is greater than 75
    {  
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, HIGH);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,LOW);
    }
    if (temperature < 75 && temperature > 50) //Determine whether value is between 50 and 75 
    {  
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,HIGH);
    }
    if (temperature < 50 && temperature > 25) //Determine whether value is between 25 and 50 
    {  
      digitalWrite(green_led, HIGH);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, LOW);
      digitalWrite(yellow_led,LOW);
    }
    if (temperature < 25)  //Determine whether value is smaller than 25 
    { 
      digitalWrite(green_led, LOW);
      digitalWrite(red_led, LOW);
      digitalWrite(blue_led, HIGH);
      digitalWrite(yellow_led,LOW);
    }
  }
  delay(1500);  //Delay 1500ms
}
```

**テスト結果**

- **赤色LED:** 100-75°C
- **黄色LED:** 75-50°C
- **緑色LED:** 50-25°C
- **青色LED:** 25-0°C

青色LEDが点灯している場合、DHT11センサーが検出した温度は0〜25°の範囲内であることを意味します。