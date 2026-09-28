# 🚦 Sygnalizacja świetlna Arduino UNO

Projekt przedstawia prosty system sygnalizacji świetlnej wykonany na płytce **Arduino UNO**. 
Układ wykorzystuje 8 diod LED — po dwie dla każdego kierunku:

- 🔴 czerwona
- 🟢 zielona

Sygnalizacja działa w dwóch naprzemiennych fazach:
- kierunki 1 i 3 mają światło zielone, a kierunki 2 i 4 czerwone,
- następnie kierunki 1 i 3 przechodzą na czerwone,
- kierunki 2 i 4 otrzymują światło zielone,
- cykl powtarza się w nieskończoność.

## 📷 Schemat układu

![Schemat połączenia Arduino](schemat.png)

## 🛠️ Wykorzystane elementy

- Arduino UNO
- 4 × czerwona dioda LED
- 4 × zielona dioda LED
- 8 × rezystor ograniczający prąd
- przewody połączeniowe

## 🔌 Podłączenie

| Kierunek | 🔴 Czerwony | 🟢 Zielony |
|----------|-------------|------------|
| 1 | D2 | D3 |
| 2 | D4 | D5 |
| 3 | D6 | D7 |
| 4 | D8 | D9 |

Każda dioda LED jest podłączona do odpowiedniego pinu Arduino przez rezystor.

## ⚙️ Zasada działania

### 1. Kierunki 1 i 3 — zielone

- 🟢 LED 1 — ON
- 🟢 LED 3 — ON
- 🔴 LED 2 — ON
- 🔴 LED 4 — ON

Ten stan trwa **5 sekund**.

### 2. Zmiana świateł

Kierunki 1 i 3 zmieniają światło z zielonego na czerwone.

Czas zmiany: **1 sekunda**.

### 3. Kierunki 2 i 4 — zielone

- 🔴 LED 1 — ON
- 🔴 LED 3 — ON
- 🟢 LED 2 — ON
- 🟢 LED 4 — ON

Ten stan trwa **5 sekund**.

### 4. Ponowna zmiana

Kierunki 2 i 4 zmieniają światło z zielonego na czerwone.

Czas zmiany: **1 sekunda**.

Po wykonaniu wszystkich etapów program zaczyna cykl od początku.

## ⏱️ Czas działania

| Etap | Czas |
|------|------|
| Kierunki 1 i 3 — zielone | 5 s |
| Zmiana | 1 s |
| Kierunki 2 i 4 — zielone | 5 s |
| Zmiana | 1 s |

Pełny cykl trwa **12 sekund**.

## 💻 Kod

```cpp
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

  // KIERUNEK 1 i 3 - ZIELONE
  // KIERUNEK 2 i 4 - CZERWONE

  digitalWrite(czerwone1, LOW);
  digitalWrite(zielone1, HIGH);

  digitalWrite(czerwone3, LOW);
  digitalWrite(zielone3, HIGH);

  digitalWrite(czerwone2, HIGH);
  digitalWrite(zielone2, LOW);

  digitalWrite(czerwone4, HIGH);
  digitalWrite(zielone4, LOW);

  delay(5000);

  // ZMIANA

  digitalWrite(zielone1, LOW);
  digitalWrite(czerwone1, HIGH);

  digitalWrite(zielone3, LOW);
  digitalWrite(czerwone3, HIGH);

  delay(1000);

  // KIERUNEK 2 i 4 - ZIELONE
  // KIERUNEK 1 i 3 - CZERWONE

  digitalWrite(czerwone2, LOW);
  digitalWrite(zielone2, HIGH);

  digitalWrite(czerwone4, LOW);
  digitalWrite(zielone4, HIGH);

  delay(5000);

  // ZMIANA

  digitalWrite(zielone2, LOW);
  digitalWrite(czerwone2, HIGH);

  digitalWrite(zielone4, LOW);
  digitalWrite(czerwone4, HIGH);

  delay(1000);
}
