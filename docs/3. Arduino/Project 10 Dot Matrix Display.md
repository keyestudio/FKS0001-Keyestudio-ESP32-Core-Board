### プロジェクト10 ドットマトリックスディスプレイ

**1. 説明**

このモジュールは8x8のLEDドットマトリックスで構成されており、各行および各列に1つずつ制御ピンがあり、LEDの明るさを調整します。Arduinoボードと接続することで、Arduinoプログラミングを通じてLEDの明るさを制御し、文字や図形を表示します。この方法により、簡単な文字、数字、図形を表示することが可能です。また、ゲーム機やスクリーンにも応用できます。

**2. 動作原理**

![](media/A37.png)

MAX7219はSPI通信を持つICで、8x8ドットマトリックスの制御に使用できます。MAX7219のSPI通信は当社のライブラリに統合されており、直接呼び出すことができます。

**ドットマトリックスモジュロ操作**

モジュロのリンクはこちら：[http://dotmatrixtool.com/#](http://dotmatrixtool.com/#)

**手順:**

1. リンクをクリックし、ドットマトリックスの高さと幅を設定します。ここでは両方とも8に設定します。

![](media/A38.png)

2. 「Byte Order」を「Column Major」に設定します。

![](media/A39.png)

3. 「Endian」を「Big Endian」に設定します。

![](media/A40.png)

4. 白いタイルをクリックして表示したいパターンを作成します（再度クリックすると選択解除）。その後「Generate」をクリックしてこのアイコンの配列を生成します。この配列をコピーしてコードに貼り付けると、パターンがドットマトリックスに表示されます。

![](media/A41.png)

**3. 配線図**

![](media/A42.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 10 Dot Matrix Display
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x30, 0x78, 0x7c, 0x3e, 0x3e, 0x7c, 0x78, 0x30};

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);  
}

void loop()
{
  for(int i=0; i < 8; i++)
  {
      lc.setRow(0,i,IMAGES[i]);
  }
}
```

**5. テスト結果**

配線を接続しコードをアップロードすると、下図のようにドットマトリックスにハートが表示されます。

![](media/A43.png)