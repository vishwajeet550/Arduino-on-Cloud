# Arduino-on-Cloud

I use Tinkercad for simulation.
First I saw the LED Blinking tutorial then I undersand the connections and code in Block and Text mode also.
In Buzer practical I make change that I replace LED with Buzer and connect Buzer with or without resistor and then build the code in Block as well as text also.     

code for Buzer insted of LED - 

// C++ code
//
void setup()
{
  pinMode(7, OUTPUT);
}

void loop()
{
  digitalWrite(7, HIGH);
  delay(1000); // Wait for 1000 millisecond(s)
  digitalWrite(7, LOW);
  delay(1000); // Wait for 1000 millisecond(s)
}

Demo Video :

https://user-images.githubusercontent.com/66294989/117432665-3ebcd180-af48-11eb-8378-5eedfc800598.mp4

Code for DC Motor :

https://user-images.githubusercontent.com/66294989/117470817-d89a7380-af74-11eb-8a46-cd75982e9460.mp4


// C++ code
//
const int potPin = A0;
const int fwdbuttonPin = 13;
const int bckbuttonPin = 12;
const int ICpin2 = 11;
const int ICpin7 = 10;

int potValue = 0;
int motorValue = 0;
int fwdbuttonState = 0;
int bckbuttonState = 0;

void setup()
{
pinMode(fwdbuttonPin, INPUT_PULLUP);

pinMode(bckbuttonPin,INPUT_PULLUP);

pinMode(ICpin2, OUTPUT);
pinMode(ICpin7, OUTPUT);
}



void loop()
{
potValue = analogRead(potPin);

motorValue = map(potValue, 0, 1023, 0, 255);

fwdbuttonState = digitalRead(fwdbuttonPin);

bckbuttonState = digitalRead(bckbuttonPin);

delay (500);
if(fwdbuttonState == LOW || bckbuttonState == LOW)
{
analogWrite(fwdbuttonState == LOW ? ICpin2 : ICpin7, motorValue);
                
digitalWrite(fwdbuttonState == LOW ? ICpin7 : ICpin2, LOW);
}

else
{
digitalWrite(ICpin2, LOW);
digitalWrite(ICpin7, LOW);
}
}
