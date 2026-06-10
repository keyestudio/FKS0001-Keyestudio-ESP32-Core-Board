### Proyecto 8 Intérprete Musical

**1. Descripción**

En este proyecto, utilizaremos un altavoz con amplificador de potencia para reproducir música. Este altavoz no solo puede tocar canciones simples, sino también interpretar lo que desees. Por lo tanto, puedes programar otros códigos interesantes en el proyecto para lograr resultados de aprendizaje espléndidos.

**2. Principio de Funcionamiento**

![](media/A28.png)

La señal eléctrica se introduce desde el pin 1 de RP1 (ajusta la intensidad de la señal, que también es el volumen del sonido).

Después de acoplarse en C4 y pasar por R5, la señal llega al pin IN- del 8002B, donde se amplifica operativamente y se envía al altavoz BEE1.

**Tabla de Comparación de Frecuencias en C**

|    Nota     | Frecuencia(Hz) |      Nota      | Frecuencia(Hz) |     Nota     | Frecuencia(Hz) |
| :---------: | :------------: | :------------: | :------------: | :----------: | :------------: |
| Bemol  1  Do |      262       | Natural  1  Do |      523       | Sostenido  1  Do |     1047      |
| Bemol  2  Re |      294       | Natural  2  Re |      587       | Sostenido  2  Re |     1175      |
| Bemol  3  Mi |      330       | Natural  3  Mi |      659       | Sostenido  3  Mi |     1319      |
| Bemol  4  Fa |      349       | Natural  4  Fa |      698       | Sostenido  4  Fa |     1397      |
| Bemol  5  So |      392       | Natural  5  So |      784       | Sostenido  5  So |     1568      |
| Bemol  6  La |      440       | Natural  6  La |      880       | Sostenido  6  La |     1760      |
| Bemol  7  Si |      494       | Natural  7  Si |      988       | Sostenido  7  Si |     1967      |

**3. Diagrama de Conexiones**

![](media/A29.png)

**4. Código de Prueba**

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

**5. Resultado de la Prueba**

Después de subir el código y encender, el amplificador reproduce circularmente tonos musicales con la frecuencia correspondiente: DO, Re, Mi, Fa, So, La, Si.

**Ajuste de volumen del amplificador de potencia:**

 **Hay un potenciómetro junto al altavoz. Podemos ajustar el volumen del altavoz girándolo.** (Nota: Por favor, use la fuerza adecuada para ajustarlo, para no dañar el potenciómetro)

![](media/A30.png)

**6. Ampliación de Conocimientos**

Vamos a tocar una canción de cumpleaños. Las conexiones permanecen sin cambios.

**Notación musical numerada:**

![](media/A31.png)

**Diagrama comparativo de Bemol, Natural y Sostenido**

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