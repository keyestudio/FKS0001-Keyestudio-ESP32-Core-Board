### プロジェクト7 アクティブブザー

**1. 説明**

アクティブブザーは、アラーム、リマインダー、またはエンターテインメントデバイスとして使用される部品で、信頼性の高い音を発します。さらに、高度に制御可能な音を発生させることができるため、プロジェクトをより面白くします。

**2. 動作原理**

![](media/A26.png)

アクティブブザーはマルチバイブレータを内蔵しているため、直流電圧のみで音を出します。ブザーのピン1はVCCに接続され、ピン2はトライオードによって制御されます。トライオードのベース（ピン1）に高レベルが供給されると、コレクタ（ピン3）とエミッタ（ピン2）がGNDに接続され、ブザーが音を発します。

逆に、ベースに低レベルを供給すると、他のピンは切断されるため、ブザーは静かなままになります。

**3. 配線図**

![](media/A27.png)

**4. テストコード**

```
 /*
  keyestudio ESP32 Inventor Learning Kit
  Project 7 Active Buzzer
  http://www.keyestudio.com
*/
int buzzer = 5; //Define buzzer connected to IO5 pin 

void setup() 
{
  pinMode(buzzer, OUTPUT);//Set the output mode 
}

void loop() 
{
  digitalWrite(buzzer, HIGH); //IO5 pin outputs a high level to cause the buzzer to emit sound 
  delay(1000);					//Delay 1000ms
  digitalWrite(buzzer, LOW); //IO5 outputs a low level to prevent the buzzer to emit sound 
  delay(1000);
}
```

**5. テスト結果**

コードをアップロードして電源を入れると、ブザーは1秒間音を出し、1秒間静かになります。