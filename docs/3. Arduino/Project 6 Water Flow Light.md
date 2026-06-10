### プロジェクト6 水流ライト

**1. 説明**

このシンプルな水流ライトプロジェクトは、電子パッケージングの学習に役立ちます。本プロジェクトでは、Arduinoボードを使ってLEDの色を指定した速度で変化させます。

**2. 配線図**

![](media/A25.png)

**3. テストコード**

水流ライトとは、LEDが左から右へ、そして右から左へと点灯することを意味します。  
この実験では連続したピンを使用しているため、"for"文を使って出力モードの設定（コード内のピンを循環変数に置き換える）だけでなく、出力も行うことができます。

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 6 Water Flow Light
  http://www.keyestudio.com
*/
void setup() 
{
  for(int i = 12;i <= 15 ;i++) //Use "for" loop statement to set IO12-IO15 pin to output mode
  {  
    pinMode(i,OUTPUT);
  }
}

void loop() 
{
  for(int i = 12; i <= 15; i++)//Use "for" loop statement to light up LED on IO12-IO15 pin in sequence 
  {		
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
  for(int i = 15; i >= 12; i--)//Use "for" loop statement to light up LED on IO15-IO12 pin in sequence 
  {		  
    digitalWrite(i,HIGH);
    delay(200);
    digitalWrite(i,LOW);
  }
}
```

**4. テスト結果**

コードをアップロードして電源を入れると、LEDが左から右へ、そして右から左へと点灯します。