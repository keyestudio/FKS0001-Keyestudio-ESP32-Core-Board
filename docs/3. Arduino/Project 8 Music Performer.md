### プロジェクト8 音楽演奏者

**1. 説明**

このプロジェクトでは、パワーアンプスピーカーを使って音楽を再生します。このスピーカーは単純な曲を演奏するだけでなく、あなたの望む演奏も可能です。したがって、プロジェクト内で他の面白いコードをプログラムして、素晴らしい学習成果を達成できます。

**2. 動作原理**

![](media/A28.png)

電気信号はRP1のピン1から入力されます（信号の強度を調整し、音量にもなります）。

C4でカップリングされ、R5を通過した後、信号は8002BのIN-ピンに到達し、そこで演算増幅されてBEE1スピーカーに出力されます。

**Cにおける周波数比較表**

|    音符     | 周波数(Hz) |      音符      | 周波数(Hz) |     音符     | 周波数(Hz) |
| :---------: | :--------: | :------------: | :--------: | :----------: | :--------: |
| フラット 1 ド |    262     | ナチュラル 1 ド |    523     | シャープ 1 ド |   1047     |
| フラット 2 レ |    294     | ナチュラル 2 レ |    587     | シャープ 2 レ |   1175     |
| フラット 3 ミ |    330     | ナチュラル 3 ミ |    659     | シャープ 3 ミ |   1319     |
| フラット 4 ファ |    349     | ナチュラル 4 ファ |    698     | シャープ 4 ファ |   1397     |
| フラット 5 ソ |    392     | ナチュラル 5 ソ |    784     | シャープ 5 ソ |   1568     |
| フラット 6 ラ |    440     | ナチュラル 6 ラ |    880     | シャープ 6 ラ |   1760     |
| フラット 7 シ |    494     | ナチュラル 7 シ |    988     | シャープ 7 シ |   1967     |

**3. 配線図**

![](media/A29.png)

**4. テストコード**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 8.1 Music Performer 
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5

void setup() 
{
  pinMode(beeppin, OUTPUT);//Define the IO5 port to output mode 
}

void loop() 
{
  tone(beeppin, 262);//Flat DO plays 500ms
  delay(500);
  tone(beeppin, 294);//Flat Re plays 500ms
  delay(500);
  tone(beeppin, 330);//Flat Mi plays 500ms
  delay(500);
  tone(beeppin, 349);//Flat Fa plays 500ms
  delay(500);
  tone(beeppin, 392);//Flat So plays 500ms
  delay(500);
  tone(beeppin, 440);//Flat La plays 500ms 
  delay(500);
  tone(beeppin, 494);//Flat Si plays 500ms 
  delay(500);
  noTone(beeppin);//Stop for 1s 
  delay(1000);
}
```

**5. テスト結果**

コードをアップロードして電源を入れると、アンプは対応する周波数の音階：ド、レ、ミ、ファ、ソ、ラ、シを繰り返し演奏します。

**パワーアンプの音量調整：**

**スピーカーの隣にポテンショメーターがあります。これを回すことでスピーカーの音量を調整できます。**（注意：ポテンショメーターを壊さないように適切な力で調整してください）

![](media/A30.png)

**6. 知識拡張**

誕生日の歌を演奏してみましょう。配線は変更しません。

**数字譜：**

![](media/A31.png)

**フラット、ナチュラル、シャープの比較図**

![](media/A32.png)

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 8.2 Music Performer
  http://www.keyestudio.com
*/
int beeppin = 5; //Define the speaker pin to IO5
// do、re、mi、fa、so、la、si

int doremi[] = {262, 294, 330, 370, 392, 440, 494,      //Falt 0-6
                523, 587, 659, 698, 784, 880, 988,      //Natural 7-13
                1047,1175,1319,1397,1568,1760,1967};    //Sharp 14-20
int happybirthday[] = {5,5,6,5,8,7,5,5,6,5,9,8,5,5,12,10,8,7,6,11,11,10,8,9,8};   //Find the number in arrey doremi[] according to the numbered musical notation 
int meter[] = {1,1,2,2,2,4, 1,1,2,2,2,4, 1,1,2,2,2,2,2, 1,1,2,2,2,4};    // Beats

void setup() 
{
  pinMode(beeppin, OUTPUT); //Set IO5 pin to output mode 
}

void loop() 
{
  for( int i = 0 ; i <= 24 ;i++)
  {       //i<=24, because there are only 24 tones in this song
    //Use tone()function to generate a waveform in "frequency"
   tone(beeppin, doremi[happybirthday[i] - 1]);
   delay(meter[i] * 200); //Wait for 1000ms
   noTone(beeppin);//Stop singing
  }
}