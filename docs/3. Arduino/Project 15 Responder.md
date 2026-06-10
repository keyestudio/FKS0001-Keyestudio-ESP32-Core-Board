### プロジェクト15 レスポンダー

**1. 説明**

このプログラム可能なレスポンダーは、Arduino開発ボードと複数のボタンを通じて信号を入力・受信し、LEDを使って回答の正誤を判定します。学生の反応能力を鍛え、問題への注意を引きつけるのに適した教材です。正解すると、回答者は多くの得点を獲得します。

さらに、教師の質問争奪の操作を簡素化し、回答の混乱を減らします。学生の学習意欲を刺激する効果も期待できます。

**2. フローチャート**

![image-20251013104115790](media/A60.png)

**3. 配線図**

![](media/A61.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 15 Responder
  http://www.keyestudio.com
*/
int blue_key = 16;	//Set blue button to connect pin D3 
int  green_key= 17;	//Set green button to connect pin D4 
int yellow_key = 18;	//Set yellow button to connect pin D5 
int red_key = 19;	//Set red button to connect pin D6 

int blue_led = 12;	//Set blue LED to connect pin D7 
int green_led = 13;	//Set green LED to connect pin D8 
int yellow_led = 14;	//Set yellow LED to connect pin D9 
int red_led = 27;	//Set red LED to connect pin D10 

void setup()
{
    //Set the pin connecting with button to input 
  pinMode(blue_key,INPUT);	
  pinMode(green_key,INPUT);
  pinMode(yellow_key,INPUT);
  pinMode(red_key,INPUT);
 	//Set the pin connecting with LED to output 
  pinMode(blue_led,OUTPUT);
  pinMode(green_led,OUTPUT);
  pinMode(yellow_led,OUTPUT);
  pinMode(red_led,OUTPUT);

}

void loop()
{
  int red_key_val = digitalRead(red_key);	//Read the red button value  
  digitalWrite(red_led,HIGH);				//Red LED lights up 
  if(red_key_val == 0)
  {				//Determine whether the red button is pressed 
    digitalWrite(red_led,LOW);		//All LED go off 
    digitalWrite(blue_led,LOW);
    digitalWrite(green_led,LOW);
    digitalWrite(yellow_led,LOW);
    delay(200);
    while(1)
    {						//while()loop 
      int blue_key_val = digitalRead(blue_key);		//Read the button value  
      int green_key_val = digitalRead(green_key);
      int yellow_key_val = digitalRead(yellow_key);
      if(blue_key_val == 0)
      {						//Determine whether the blue button is pressed 
        digitalWrite(blue_led,HIGH);				//Blue LED lights up 
        break;										//Exit loop
      }
      if(green_key_val == 0)
      {
        digitalWrite(green_led,HIGH);
        break;
      }
      if(yellow_key_val == 0)
      {
        digitalWrite(yellow_led,HIGH);
        break;
      }
    }
  }
}
```

**5. テスト結果**

クイックアンサーゲームをシミュレートしてみましょう。

赤いボタンを押すとすべてのLEDが消灯します。その後、黄色、緑、青のボタンを押すことで対応するLEDが点灯します。最初にLEDが点灯した人が最初に回答できます。
