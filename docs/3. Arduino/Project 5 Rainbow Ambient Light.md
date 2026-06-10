### Projet 5 Lumière d'Ambiance Arc-en-Ciel

**1. Description**

La LED Arduino 2812RGB est une lumière programmable colorée et onirique, dont la couleur, la luminosité et le rythme sont réglables. Cette lumière d'ambiance arc-en-ciel peut être utilisée comme décoration dynamique à volonté. Vous pouvez également la contrôler pour la faire "danser avec la musique". Important, elle peut être améliorée en tant qu'alarme. Son capteur intégré détecte l'environnement ambiant pour avertir les utilisateurs en changeant sa couleur, sa luminosité et son rythme.

**2. Principe de Fonctionnement**

![](media/A22.png)

Le protocole de données adopte un mode de communication à code retour à zéro sur une seule ligne. Après la réinitialisation du pixel à la mise sous tension, la borne DIN reçoit les données du contrôleur. Les premières données de 24 bits reçues seront extraites par le premier pixel et envoyées au registre de données interne.

Les données restantes seront amplifiées par un circuit d'amplification et transmises via la sortie DOUT au pixel suivant en cascade. En traversant les pixels, le signal diminue de 24 bits à chaque fois.

De plus, le pixel utilise une technologie d'auto-mise en forme et de retransmission, de sorte que le nombre de pixels en cascade est uniquement limité par la vitesse de transmission du signal.

**3. Schéma de Câblage**

![](media/A23.png)

**4. Code de Test**

```
/*
  keyestudio ESP32 Inventor Learning Kit 
  Project 5.1  Rainbow Ambient Light
  http://www.keyestudio.com
*/
//Add 2812RGB library file
#include <NeoPixel_ESP32.h>
#define PIN 15

Adafruit_NeoPixel strip = Adafruit_NeoPixel(6, PIN);  //Defines the instance strip and assigns the RGB LED number pins to the library code

void setup() 
{
  strip.begin();        //Activate RGB LED
  strip.show(); // Refresh the display
}

void loop() 
{
  strip.setPixelColor(0, strip.Color(255, 0, 0));       //The frist RGB LED is red 
  strip.setPixelColor(1, strip.Color(0, 255, 0));       //The second RGB LED is green  
  strip.setPixelColor(2, strip.Color(0, 0, 255));       //The third RGB LED is blue 
  strip.setPixelColor(3, strip.Color(255, 255, 0));     //The fourth RGB LED is yellow 
  strip.setPixelColor(4, strip.Color(255, 0, 255));     //The fifth RGB LED is purple 
  strip.setPixelColor(5, strip.Color(255, 255, 255));   //The sixth RGB LED is white 
  strip.show();       //Refresh the display
  delay(100);         //Give a delay to save the stability of the display
}
```

**5. Résultat du Test**

Après avoir téléversé le code et mis sous tension, la LED s'allumera en différentes couleurs.

De gauche à droite :

- La première LED RGB est rouge  
- La deuxième LED RGB est verte  
- La troisième LED RGB est bleue  
- La quatrième LED RGB est jaune  
- La cinquième LED RGB est violette  
- La sixième LED RGB est blanche  

![](media/A24.png)

**6. Code Étendu**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
  Project 5.2  Rainbow Ambient Light
  http://www.keyestudio.com
*/
//Add 2812RGB library file
#include <NeoPixel_ESP32.h>
#define PIN 15
Adafruit_NeoPixel strip = Adafruit_NeoPixel(6, PIN, NEO_GRB + NEO_KHZ800);

void setup() 
{
  strip.begin();
  strip.show(); // Initialize all pixels to 'off'
}

void loop() 
{
  // Some example procedures showing how to display to the pixels:
  colorWipe(strip.Color(255, 0, 0), 50); // Red
  colorWipe(strip.Color(0, 255, 0), 50); // Green
  colorWipe(strip.Color(0, 0, 255), 50); // Blue
  // Send a theater pixel chase in...
  theaterChase(strip.Color(127, 127, 127), 50); // White
  theaterChase(strip.Color(127,   0,   0), 50); // Red
  theaterChase(strip.Color(  0,   0, 127), 50); // Blue

  rainbow(20);
  rainbowCycle(20);
  theaterChaseRainbow(50);
}

// Fill the dots one after the other with a color
void colorWipe(uint32_t c, uint8_t wait) 
{
  for(uint16_t i=0; i<strip.numPixels(); i++) 
  {
      strip.setPixelColor(i, c);
      strip.show();
      delay(wait);
  }
}

void rainbow(uint8_t wait) 
{
  uint16_t i, j;

  for(j=0; j<256; j++) 
  {
    for(i=0; i<strip.numPixels(); i++) 
    {
      strip.setPixelColor(i, Wheel((i+j) & 255));
    }
    strip.show();
    delay(wait);
  }
}

// Slightly different, this makes the rainbow equally distributed throughout
void rainbowCycle(uint8_t wait) 
{
  uint16_t i, j;
  for(j=0; j<256*5; j++) // 5 cycles of all colors on wheel
  { 
    for(i=0; i< strip.numPixels(); i++) 
    {
      strip.setPixelColor(i, Wheel(((i * 256 / strip.numPixels()) + j) & 255));
    }
    strip.show();
    delay(wait);
  }
}

//Theatre-style crawling lights.
void theaterChase(uint32_t c, uint8_t wait) 
{
  for (int j=0; j<10; j++) //do 10 cycles of chasing
  {  
    for (int q=0; q < 3; q++) 
    {
      for (int i=0; i < strip.numPixels(); i=i+3) 
      {
        strip.setPixelColor(i+q, c);    //turn every third pixel on
      }
      strip.show();
      delay(wait);
      for (int i=0; i < strip.numPixels(); i=i+3) 
      {
        strip.setPixelColor(i+q, 0);        //turn every third pixel off
      }
    }
  }
}

//Theatre-style crawling lights with rainbow effect
void theaterChaseRainbow(uint8_t wait) 
{
  for (int j=0; j < 256; j++) // cycle all 256 colors in the wheel
  {     
    for (int q=0; q < 3; q++) 
    {
        for (int i=0; i < strip.numPixels(); i=i+3) 
        {
          strip.setPixelColor(i+q, Wheel( (i+j) % 255));    //turn every third pixel on
        }
        strip.show();
        delay(wait);
        for (int i=0; i < strip.numPixels(); i=i+3) 
        {
          strip.setPixelColor(i+q, 0);        //turn every third pixel off
        }
    }
  }
}

// Input a value 0 to 255 to get a color value.
// The colours are a transition r - g - b - back to r.
uint32_t Wheel(byte WheelPos) 
{
  if(WheelPos < 85) 
  {
  	return strip.Color(WheelPos * 3, 255 - WheelPos * 3, 0);
  } 
  else if(WheelPos < 170) 
  {
      WheelPos -= 85;
      return strip.Color(255 - WheelPos * 3, 0, WheelPos * 3);
  } 
  else 
  {
      WheelPos -= 170;
      return strip.Color(0, WheelPos * 3, 255 - WheelPos * 3);
  }
}
```

**7. Résultat du Test**

Après avoir téléversé le code et mis sous tension, la LED s'allumera en différentes couleurs et réalisera un spectacle lumineux.