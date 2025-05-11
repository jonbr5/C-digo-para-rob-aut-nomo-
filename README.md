/*int LEDVermelho = 4;
int LEDAmarelo = 5;
int LEDVerde = 6;

void setup() {

pinMode (LEDVermelho, OUTPUT);
pinMode (LEDAmarelo, OUTPUT);
pinMode (LEDVerde, OUTPUT);

}

void loop() {

digitalWrite (LEDVerde, HIGH);
delay(2000);
digitalWrite (LEDVerde, LOW);
digitalWrite (LEDAmarelo, HIGH);
delay(1000);
digitalWrite (LEDAmarelo, LOW);
digitalWrite (LEDVerde, HIGH);
delay (3000);
digitalWrite (LEDVerde, LOW);

}*/

#include <Servo.h>

Servo myservo;  

int pos = 0;    


int LEDVermelho = 4;
int LEDAmarelo = 5;
int LEDVerde = 6;


void setup()
{
myservo.attach(10);  

Serial.begin(9600);
pinMode (LEDVermelho, OUTPUT);
pinMode (LEDAmarelo, OUTPUT);
pinMode (LEDVerde, OUTPUT);  }


 
void semaforo1()
{ 

           if (digitalRead(LEDVermelho) == LOW  && digitalRead(LEDVerde) == LOW & digitalRead(LEDAmarelo ==LOW)   || digitalRead(LEDVermelho) == HIGH  && digitalRead(LEDVerde) ==  LOW && digitalRead(LEDAmarelo ==LOW))
  {
     digitalWrite (LEDVermelho, LOW);
     digitalWrite (LEDVerde, HIGH);
     digitalWrite (LEDAmarelo, LOW);
     delay(3000); 
  

           }
   
     if (digitalRead(LEDVermelho) == LOW  && digitalRead(LEDVerde) ==  HIGH && digitalRead(LEDAmarelo ==LOW))
      {
     digitalWrite (LEDVermelho, LOW);
     digitalWrite (LEDVerde, LOW);
     digitalWrite (LEDAmarelo, HIGH);
  	 delay(1000);
       for (pos = 90; pos >= 0; pos -= 90) { 
          myservo.write(pos);  
         Serial.println("Cancela aberta");
 }
  }
 if (digitalRead(LEDVermelho) == LOW  && digitalRead(LEDVerde) ==  LOW && digitalRead(LEDAmarelo ==HIGH))
      {
     digitalWrite (LEDVermelho, HIGH);
     digitalWrite (LEDVerde, LOW);
    digitalWrite (LEDAmarelo, LOW);
   	delay(2000);
   for (pos = 0; pos <= 90; pos += 90) { 
          myservo.write(pos);  
     Serial.println("Cancela fechada");
 }
    
  }
  
}

void loop() 
{
  
  
  return semaforo1();
   

}
