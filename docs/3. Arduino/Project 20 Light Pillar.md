### Progetto 20 Pilastro di Luce

**1. Descrizione**

La resistenza (inferiore a 1KΩ) della fotoresistenza varia in base alla luce, quindi può controllare la luminosità della matrice di punti. Durante il controllo, colleghiamo questa resistenza a un pin analogico sulla scheda per monitorare la variazione della resistenza. In questo modo, la luce controlla automaticamente la luminosità del display.

Inoltre, la fotoresistenza è ampiamente utilizzata nella vita quotidiana. Ad esempio, una tenda si apre o si chiude automaticamente in base all'intensità della luce esterna.

**2. Principio di Funzionamento**

![](media/B8.png)

![](media/B9.png)

Quando è completamente al buio, la resistenza è pari a 0,2MΩ, e la tensione al terminale di segnale (punto 2) si avvicina a 0V. Più la luce è intensa, più la resistenza e la tensione saranno basse.

**3. Schema di Collegamento**

![](media/B10.png)

**4. Codice di Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.1 Light Pillar
  http://www.keyestudio.com
*/
int light = 34;      //Define light to IO34

void setup() 
{
  // put your setup code here, to run once:
  Serial.begin(9600);		//Set baud rate to 9600
}

void loop() 
{
  // put your main code here, to run repeatedly:
  int value = analogRead(light);	//Read IO34 and assign it to the variable value
  Serial.println(value);		//Print the variable value and wrap it around 
  delay(200);
}
```

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, aprire il monitor seriale impostando la velocità di trasmissione a 9600; verrà visualizzato il valore analogico, nell'intervallo da 0 a 4095. Variando l'intensità della luce intorno al sensore, si modifica il valore letto.

![](media/B11.png)

**6. Approfondimento**

Utilizzeremo questa fotoresistenza per rilevare l'intensità della luce ambientale. Le due colonne centrali sono incluse in questo esperimento per rappresentare l'intensità luminosa. Più è forte, più LED si accenderanno. Questo forma un "pilastro di luce".

- **Schema di Collegamento：**

![](media/B12.png)

- **Codice：**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 20.2 Light Pillar
  http://www.keyestudio.com
*/

#include "LedControl.h"
int DIN = 23;
int CLK = 18;
int CS = 15;
LedControl lc=LedControl(DIN,CLK,CS,1);
const byte IMAGES[8] = {0x01,0x03,0x07,0x0F,0x1F,0x3F,0x7F,0xFF}; //Data of light pillar

int light = 34;

void setup() 
{
  lc.shutdown(0,false);
  // Set brightness to a medium value
  lc.setIntensity(0,8);
  // Clear the display
  lc.clearDisplay(0);
  pinMode(light,INPUT);  
}

void loop()
{
  int value = analogRead(light);
  int temp = map(value,0,4095,0,7);  //Convert the range of analog values to 0-7
  lc.setRow(0,3,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 3
  lc.setRow(0,4,IMAGES[temp]);      //Display the value of the array IMAGES[temp] in column 4
}
```

- **Risultato del Test**

Più la luce vicino alla fotoresistenza è intensa, più alta sarà la colonna luminosa della matrice LED.

![](media/B13.png)