### プロジェクト17 侵入警報

**1. 説明**

この侵入警報システムは、住宅や小規模オフィス内の侵入者を検知し、ホストに対して適時に対策を促すことができます。

本プロジェクトでは、センサーが特定のエリアを監視します。Arduinoボード上のデバイスが、そのゾーンで動きを検知するとLEDを点灯させ、ブザーを鳴らして注意を促します。

実際、このモジュールは実用性が高く、設置が簡単でコストも低いです。家庭やオフィスだけでなく、工場、倉庫、市場などにも適用でき、財産の安全を大いに守ります。

**2. 動作原理**

![](media/A64.png)

人体（37°C）は常に波長約10μmの赤外線を放射しており、これはセンサーが検知する波長に近いです。

このため、このモジュールは人体の動きを検知できます。動きがある場合、PIRセンサーは約3秒間ハイレベルを出力し、動きがなければローを出力します。

**3. 配線図**

![](media/A65.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.1 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;    //Define IO5 as PIR sensor pin 

void setup() 
{
  pinMode(pir,INPUT);   //Set IO5 pin to input 
  Serial.begin(9600);
}

void loop() 
{
  int pir_val = digitalRead(pir); 	//Read the PIR result and assign it to pir_val 
    Serial.print("pir_val:"); //Print “pir_val”
	Serial.println(pir_val);
    delay(500);
}
```

**5. テスト結果**

配線を接続しコードをアップロードした後、シリアルモニターを開きボーレートを9600に設定すると、シリアルポートにPIRの値が表示されます。PIRセンサーが人を検知すると、1が表示されます。

![](media/A66.png)

**6. 知識拡張**

侵入警報を作りましょう。PIRセンサーが人を検知すると、LEDが点灯しブザーが鳴ります。検知しない場合は、LEDは消灯しブザーは鳴りません。

- **フローチャート：**

![](media/A67.png)

- **配線図：**

![](media/A68.png)

- **コード：**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 17.2 Invasion Alarm
  http://www.keyestudio.com
*/
int pir = 5;		//Set PIR sensor pin to IO5
int red_led = 18;	//Set red LED to pin IO18
int buzz = 19;		//Set buzzer to pin IO19

void setup() 
{
  // put your setup code here, to run once:
  pinMode(pir,INPUT);		//Set PIR pin to input mode 
  pinMode(red_led,OUTPUT);	//Set LED pin to output mode  
  pinMode(buzz,OUTPUT);		//Set buzzer pin to output mode 
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int pir_val = digitalRead(pir);
  if(pir_val == 1)
  {
    digitalWrite(red_led,HIGH);
    digitalWrite(buzz,HIGH);
  }
  else
  {
    digitalWrite(red_led,LOW);
    digitalWrite(buzz,LOW);
  }
}
```

**テスト結果**

PIRセンサーが近くの人を検知すると、赤色LEDが点灯しブザーが鳴ります。