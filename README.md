// Passive Buzzer: Shave and a Haircut (looping)
// Buzzer + 220Ω resistor -> pin 8 ; Buzzer - -> GND

const int BUZZER_PIN = 3;

// Frequencies (Hz)
#define NOTE_C4  262
#define NOTE_D4  294
#define NOTE_E4  330
#define NOTE_F4  349
#define NOTE_G4  392
#define NOTE_A4  440
#define NOTE_B4  494
#define NOTE_C5  523

// Tempo
int tempo = 120;  // beats per minute
int quarter = 60000 / tempo;  // ms per quarter note

// "Shave and a Haircut, Two Bits"
int melody[] = {
  NOTE_G4, NOTE_E4, NOTE_F4, NOTE_D4,
  NOTE_E4, 0,       NOTE_C4, NOTE_C5
};

int noteDurations[] = {
  4, 4, 4, 4,
  4, 4, 4, 2
};
// 4 = quarter, 2 = half

void setup() {
  pinMode(BUZZER_PIN, OUTPUT);
}

void loop() {
  for (int i = 0; i < 8; i++) {
    int duration = quarter * (4.0 / noteDurations[i]);
    if (melody[i] > 0) {
      tone(BUZZER_PIN, melody[i], duration * 0.9);
    }
    delay(duration);
    noTone(BUZZER_PIN);
  }

  delay(1000); // pause before repeating
}
