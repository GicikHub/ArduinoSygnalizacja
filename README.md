# ArduinoSygnalizacja

// LED 1
int czerwone1 = 2;
int zielone1  = 3;

// LED 2
int czerwone2 = 4;
int zielone2  = 5;

// LED 3
int czerwone3 = 6;
int zielone3  = 7;

// LED 4
int czerwone4 = 8;
int zielone4  = 9;

void setup() {
  pinMode(czerwone1, OUTPUT);
  pinMode(zielone1, OUTPUT);

  pinMode(czerwone2, OUTPUT);
  pinMode(zielone2, OUTPUT);

  pinMode(czerwone3, OUTPUT);
  pinMode(zielone3, OUTPUT);

  pinMode(czerwone4, OUTPUT);
  pinMode(zielone4, OUTPUT);
}

void loop() {

  // =================================
  // KIERUNEK 1 i 3 - ZIELONE
  // KIERUNEK 2 i 4 - CZERWONE
  // =================================

  digitalWrite(czerwone1, LOW);
  digitalWrite(zielone1, HIGH);

  digitalWrite(czerwone3, LOW);
  digitalWrite(zielone3, HIGH);

  digitalWrite(czerwone2, HIGH);
  digitalWrite(zielone2, LOW);

  digitalWrite(czerwone4, HIGH);
  digitalWrite(zielone4, LOW);

  delay(5000);


  // =================================
  // ZMIANA
  // =================================

  digitalWrite(zielone1, LOW);
  digitalWrite(czerwone1, HIGH);

  digitalWrite(zielone3, LOW);
  digitalWrite(czerwone3, HIGH);

  delay(1000);


  // =================================
  // KIERUNEK 2 i 4 - ZIELONE
  // KIERUNEK 1 i 3 - CZERWONE
  // =================================

  digitalWrite(czerwone2, LOW);
  digitalWrite(zielone2, HIGH);

  digitalWrite(czerwone4, LOW);
  digitalWrite(zielone4, HIGH);

  delay(5000);


  // =================================
  // ZMIANA
  // =================================

  digitalWrite(zielone2, LOW);
  digitalWrite(czerwone2, HIGH);

  digitalWrite(zielone4, LOW);
  digitalWrite(czerwone4, HIGH);

  delay(1000);
}
