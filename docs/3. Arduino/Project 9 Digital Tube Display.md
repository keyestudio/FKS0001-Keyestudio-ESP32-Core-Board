### プロジェクト9 デジタルチューブディスプレイ

**1. 説明**

この4桁のデジタルチューブディスプレイは、カウントや時間を表示するためのデバイスで、0～9の数字および簡単な文字を表示できます。4つのデジタルチューブで構成されており、それぞれに7つの発光ダイオード（LED）が搭載されています。

さらに、ピンをArduino開発ボードに接続することで、時計機能やゲームの保存など複数の機能を実現できます。

**2. 動作原理**

![](media/A33.png)

TM1650はIICプロトコルを利用し、2本のバスライン（SDAとSCL）を採用しています。

**データコマンド:** 0x48  
このコマンドはTM1650にデジタルチューブを点灯させるよう指示し、キーのスキャンは行いません。

**表示コマンド:**

![](media/A34.png)

実際には1バイトのデータで、異なるビットが異なる機能を表します。  
**bit[6:4]:** LEDの明るさを設定します。000は最も明るいことを示します。  
**bit[3]:** 小数点の有無を決定します。  
**bit[0]:** 表示のオン・オフを決定します。

**デジタルチューブの点灯**  
例として、小数点なしのレベル8の明るさは0x05を示します。  
手順：開始信号 — 0x48送信 — スレーブデバイス受信 — 0x05送信 — スレーブデバイス受信 — 終了信号  
点灯後は、デジタルチューブの機能が確定しているため、0x48を繰り返し送信する必要はありません。  
また、明るさや表示方法は複数のデータを一括で列挙できるため、分かりやすく省スペースです。

**デジタルチューブの消灯**  
手順：開始信号 — 0x48送信 — スレーブデバイス受信 — 0x00送信 — スレーブデバイス受信 — 終了信号

**デジタルチューブの数字表示**  
まずTM1650に特定のチューブに数字を表示するよう指示します。すると数字が表示されます。8ビットは8つのセグメントに対応し、1は点灯、0は消灯を意味します。対応関係に疑問がある場合は、ループでビットごとに点灯させて確認できます。

例えば、ビット1が点灯して8を表示する場合、データは0x68です。小数点がある場合は、0x7fを送信すると8が表示されます。  
手順：開始信号 — 0x68送信 — スレーブデバイス受信 — 0x7f送信 — スレーブデバイス受信 — 終了信号  
結果：ビット1に8が表示されます。

便宜上、0～9に対応する値の配列を作成できます。さらに改良すれば、数字表示、明るさ調整、小数点やチューブのシフトが可能です。

**3. 配線図**

![](media/A35.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.1 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
    DigitalTube.displayFloatNum(9999);   //Values or variables added to the parentheses can be displayed through the digital tube 
}
```

**5. テスト結果**

配線を接続しコードをアップロードすると、デジタルチューブディスプレイに「9999」が表示されます。下図参照。

![](media/A36.png)

**6. 拡張コード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 9.2 Digital Tube Display 
  http://www.keyestudio.com
*/
#include "TM1650.h"
#define CLK 22    //pins definitions for TM1650 and can be changed to other ports       
#define DIO 21
TM1650 DigitalTube(CLK,DIO);

void setup()
{
  for(char b=0;b<4;b++)
  {
    DigitalTube.clearBit(b);      //DigitalTube.clearBit(0 to 3); Clear bit display.
  }
}

void loop()
{
  for(int num=0; num<10000; num++)
  {   //numが10000未満の場合、1サイクルごとにnumが1ずつ増加します
    DigitalTube.displayFloatNum(num);   //括弧内の値や変数をデジタルチューブで表示可能
    delay(100);
  }
}
```

**7. テスト結果**

コードをアップロード後、デジタルチューブは「for」ループにより1～9999を表示します。