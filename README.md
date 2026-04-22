int red = 2;
int yellow = 3;
int green = 4;
int button = 7;

bool systemOn = false;
int lastButtonState = LOW;

void setup() {
  pinMode(red, OUTPUT);
  pinMode(yellow, OUTPUT);
  pinMode(green, OUTPUT);
  pinMode(button, INPUT);
}

void loop() {
  int buttonState = digitalRead(button);

  if (buttonState == HIGH && lastButtonState == LOW) {
    systemOn = !systemOn;
    delay(200);
  }

  lastButtonState = buttonState;

  if (systemOn) {
    digitalWrite(green, HIGH);
    digitalWrite(yellow, LOW);
    digitalWrite(red, LOW);
    delay(3000);

    digitalWrite(green, LOW);
    digitalWrite(yellow, HIGH);
    digitalWrite(red, LOW);
    delay(1000);

    digitalWrite(green, LOW);
    digitalWrite(yellow, LOW);
    digitalWrite(red, HIGH);
    delay(3000);
  } else {
    digitalWrite(red, LOW);
    digitalWrite(yellow, LOW);
    digitalWrite(green, LOW);
  }
}
