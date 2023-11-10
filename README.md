# Arduiono

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
