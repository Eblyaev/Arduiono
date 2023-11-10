# Arduiono

https://github.com/wilmouths/RGBLed

```c++
#define LED3 8
#define LED2 9
#define LED1 10
#define BUTTON 7
 bool btnState = false;
void setup() {
  pinMode(LED1, OUTPUT);
  pinMode(LED2, OUTPUT);
  pinMode(LED3, OUTPUT);
  pinMode(BUTTON, INPUT);
 
}

void loop() {

  int btnVal = digitalRead(BUTTON);
  
  if(btnVal == 0) {
    btnState = !btnState;
  }
  if (btnState) {
    digitalWrite(LED1, HIGH);
    digitalWrite(LED2, HIGH);
    digitalWrite(LED3, HIGH);
  }
  else {
    digitalWrite(LED1, LOW);
    digitalWrite(LED2, LOW);
    digitalWrite(LED3, LOW);
  }
}

```
```c++

const int PIN_RED   = 5;
const int PIN_GREEN = 6;
const int PIN_BLUE  = 9;

void setup() {
  pinMode(PIN_RED,   OUTPUT);
  pinMode(PIN_GREEN, OUTPUT);
  pinMode(PIN_BLUE,  OUTPUT);
}

void loop() {

  analogWrite(PIN_RED,   0);
  analogWrite(PIN_GREEN, 0);
  analogWrite(PIN_BLUE,  255);

  delay(1000); 

  analogWrite(PIN_RED,   255);
  analogWrite(PIN_GREEN, 0);
  analogWrite(PIN_BLUE,  0);

  delay(1000); 

  analogWrite(PIN_RED,   0);
  analogWrite(PIN_GREEN, 255);
  analogWrite(PIN_BLUE,  0);

  delay(1000); 
}

```

```c++
#include <RGBLed.h>

#define RED_PIN 10
#define BLUE_PIN 9
#define GREEN_PIN 8

RGBLed led(RED_PIN, GREEN_PIN, BLUE_PIN, RGBLed::COMMON_ANODE);

void setup() {
  pinMode(RED_PIN, OUTPUT);


}

void loop() {
  
  led.setColor(0, 0, 255);
  led.flash(0, 0, 255, 100);
  led.brightness(0, 0, 255, 10);
}

```
http://wiki.amperka.ru/%D0%BF%D1%80%D0%BE%D0%B4%D1%83%D0%BA%D1%82%D1%8B:troyka-temperature-sensor
```c++

    #include <TroykaThermometer.h>
    
    #define LED 7

    TroykaThermometer thermometer(A0);
     
    void setup()
    {
      Serial.begin(9600);
    }
     
    void loop(){
      if (thermometer.getTemperatureC () < 15){
        digitalWrite(LED, HIGH);
      }
      thermometer.read();
     
      Serial.print("Temperature is ");
      Serial.print(thermometer.getTemperatureC());
      Serial.println(" C");
    
      Serial.print("Temperature is ");
      Serial.print(thermometer.getTemperatureK());
      Serial.println(" K");
     
      Serial.print("Temperature is ");
      Serial.print(thermometer.getTemperatureF());
      Serial.println(" F");
      delay(1000);
    }
```
http://wiki.amperka.ru/%D0%BF%D1%80%D0%BE%D0%B4%D1%83%D0%BA%D1%82%D1%8B:troyka:quad-display-v2
```c++
    #include <QuadDisplay2.h>
    #include <TroykaThermometer.h>
    TroykaThermometer thermometer(A0);
    QuadDisplay qd(9);

     
    void setup()
    {
      Serial.begin(9600);
      qd.begin();
    }
     
    void loop()
    { 
      thermometer.read();
      qd.displayTemperatureC(thermometer.getTemperatureC());
      delay(1000);
     
    }
```
http://wiki.amperka.ru/%D0%BF%D1%80%D0%BE%D0%B4%D1%83%D0%BA%D1%82%D1%8B:troyka-vibration-sensor
```c++
#define VIBRO_PIN             A5
#define VIBRO_INTEGRATED_PIN  A4
 #include <QuadDisplay2.h>
#include <TroykaThermometer.h>
TroykaThermometer thermometer(A0);
QuadDisplay qd(9);
void setup() 
{
  Serial.begin(9600);
  qd.begin();
}
 
void loop()
{
  thermometer.read();
  int vibroValue = analogRead(VIBRO_PIN);

  int integratedVibroValue = analogRead(VIBRO_INTEGRATED_PIN);
  Serial.print(vibroValue);
  Serial.print("\t\t");
  Serial.println(integratedVibroValue);

 if (thermometer.getTemperatureC() > 25 && integratedVibroValue >50) {
    qd.displayDigits(QD_F, QD_U, QD_C, QD_K); 
    delay(1000);
 }
 }
```
