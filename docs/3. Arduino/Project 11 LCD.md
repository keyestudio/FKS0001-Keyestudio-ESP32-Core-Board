### Progetto 11 LCD

**1. Descrizione**

Arduino I2C 1602 LCD è un dispositivo ausiliario comunemente usato per le schede di sviluppo MCU per collegarsi a sensori e moduli esterni. Presenta uno schermo LCD a 16 caratteri di larghezza e 2 linee con luminosità regolabile. Questo modulo programmabile è comodo per la modifica, visualizzazione e gestione dei dati. Inoltre, può mostrare non solo caratteri e cifre, ma anche valori dei sensori, come temperatura, umidità o pressione.

Grazie alla sua versatilità, il display è ampiamente utilizzato in molti settori, inclusi prodotti per la casa intelligente, sistemi di monitoraggio industriale, sistemi di controllo robotico e sistemi elettronici automobilistici.

**2. Principio di funzionamento**

![](media/A44.png)

Il principio è lo stesso della comunicazione IIC. Le funzioni di base sono state incapsulate in librerie in modo che possano essere richiamate direttamente. Se sei interessato, puoi approfondire i principi di funzionamento sottostanti.

**3. Schema di collegamento**

![](media/A45.png)

**4. Codice di prova**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 11 LCD
  http://www.keyestudio.com
*/
#include <Wire.h>
#include <LiquidCrystal_I2C.h>
LiquidCrystal_I2C lcd(0x27,16,2); // set the LCD address to 0x27 for a 16 chars and 2 line display

void setup()
{
    lcd.init(); // initialize the lcd
    // Print a message to the LCD.
    lcd.backlight();		//Turn on the LCD backlight 
    lcd.setCursor(2,0);		//Set the display position 
    lcd.print("Hello,world!");		//LCD displays "Hello, world!"
    lcd.setCursor(2,1);	
    lcd.print("keyestudio!");		//LCD displays "keyestudio!"
}

void loop()
{
}
```

**5. Risultato del test**

Dopo aver collegato i fili e caricato il codice, accendi l’LCD, verranno visualizzati "Hello, world!" e "keyestudio!" sul display.

![](media/A46.png)

Se i caratteri risultano poco chiari, regola il potenziometro della retroilluminazione con un piccolo cacciavite a taglio (usa una forza adeguata per la regolazione). Collega un’alimentazione esterna se necessario.

![](media/A47.png)

![](media/A48.png)