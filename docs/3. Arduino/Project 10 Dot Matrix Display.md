### Progetto 10 Display a Matrice di Punti

**1. Descrizione**

Questo modulo consiste in una matrice di LED 8x8 con un pin di controllo per ogni riga e colonna per regolare la luminosità dei LED. Collegandolo alla scheda Arduino, la luminosità dei LED viene controllata per visualizzare caratteri e figure tramite programmazione Arduino. In questo modo, è possibile visualizzare caratteri semplici, numeri e figure. Può essere applicato anche in macchine da gioco o schermi.

**2. Principio di Funzionamento**

![](media/A37.png)

MAX7219 è un IC con comunicazione SPI e può essere utilizzato per controllare la matrice di punti 8x8. La comunicazione SPI del MAX7219 è integrata nelle nostre librerie e può essere richiamata direttamente.

**Funzionamento del Modulo Matrice di Punti**

Clicca sul link per il Modulo ：[http://dotmatrixtool.com/#](http://dotmatrixtool.com/#)

**Passaggi:**

1. Clicca sul link e imposta l'altezza e la larghezza della matrice di punti. Qui impostiamo entrambi a 8.

![](media/A38.png)

2. Imposta "Byte Order" su "Column Major".

![](media/A39.png)

3. Imposta "Endian" su "Big Endian".

![](media/A40.png)

4. Clicca sulle tessere bianche per formare il motivo desiderato (clicca di nuovo per deselezionare), quindi clicca su "Generate" per generare un array per questa icona. Copia questo array e incollalo nel codice, così il motivo verrà visualizzato sulla matrice di punti.

![](media/A41.png)

**3. Schema di Collegamento**

![](media/A42.png)

**4. Codice di Test**

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
  // Imposta la luminosità a un valore medio
  lc.setIntensity(0,8);
  // Pulisce il display
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

**5. Risultato del Test**

Dopo aver collegato i fili e caricato il codice, un cuore verrà visualizzato sulla matrice di punti, come mostrato di seguito.

![](media/A43.png)