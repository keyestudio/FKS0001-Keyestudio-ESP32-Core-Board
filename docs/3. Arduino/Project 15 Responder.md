### Project 15 Responder

**1. Beschrijving**

Deze programmeerbare responder ontvangt en verzendt signalen via een Arduino-ontwikkelbord en een groep knoppen, en beoordeelt de juistheid van antwoorden via een LED. Het is een goed hulpmiddel om de reactievermogen van studenten te oefenen en hun aandacht op vragen te richten. Als het antwoord correct is, krijgt de deelnemer veel punten.

Bovendien vereenvoudigt het de bediening van vraaggrijpers door docenten en vermindert het rommelige antwoorden. Het kan zelfs de interesse van studenten in leren stimuleren.

**2. Stroomschema**

![image-20251013104115790](media/A60.png)

**3. Aansluitschema**

![](media/A61.png)

**4. Testcode**

```
/*
  keyestudio ESP32 Inventor Learning Kit  
   Project 15 Responder
  http://www.keyestudio.com
*/
int blue_key = 16;	//Set blue button to connect pin D3 
int  green_key= 17;	//Set green button to connect pin D4 
int yellow_key = 18;	//Set yellow button to connect pin D5 
int red_key = 19;	//Set red button to connect pin D6 

int blue_led = 12;	//Set blue LED to connect pin D7 
int green_led = 13;	//Set green LED to connect pin D8 
int yellow_led = 14;	//Set yellow LED to connect pin D9 
int red_led = 27;	//Set red LED to connect pin D10 

void setup()
{
    //Set the pin connecting with button to input 
  pinMode(blue_key,INPUT);	
  pinMode(green_key,INPUT);
  pinMode(yellow_key,INPUT);
  pinMode(red_key,INPUT);
 	//Set the pin connecting with LED to output 
  pinMode(blue_led,OUTPUT);
  pinMode(green_led,OUTPUT);
  pinMode(yellow_led,OUTPUT);
  pinMode(red_led,OUTPUT);

}

void loop()
{
  int red_key_val = digitalRead(red_key);	//Read the red button value  
  digitalWrite(red_led,HIGH);				//Red LED lights up 
  if(red_key_val == 0)
  {				//Determine whether the red button is pressed 
    digitalWrite(red_led,LOW);		//All LED go off 
    digitalWrite(blue_led,LOW);
    digitalWrite(green_led,LOW);
    digitalWrite(yellow_led,LOW);
    delay(200);
    while(1)
    {						//while()loop 
      int blue_key_val = digitalRead(blue_key);		//Read the button value  
      int green_key_val = digitalRead(green_key);
      int yellow_key_val = digitalRead(yellow_key);
      if(blue_key_val == 0)
      {						//Determine whether the blue button is pressed 
        digitalWrite(blue_led,HIGH);				//Blue LED lights up 
        break;										//Exit loop
      }
      if(green_key_val == 0)
      {
        digitalWrite(green_led,HIGH);
        break;
      }
      if(yellow_key_val == 0)
      {
        digitalWrite(yellow_led,HIGH);
        break;
      }
    }
  }
}
```

**5. Testresultaat**

Laten we een snel-antwoordspel simuleren.

Druk op de rode knop om alle LED-lampjes uit te schakelen. Daarna kunnen we de gele, groene en blauwe knoppen gebruiken om de bijbehorende LED-lampjes aan te zetten. Degene wiens LED-lampje als eerste aangaat, mag als eerste antwoorden.