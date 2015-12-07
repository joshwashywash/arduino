# arduino
codes and sketches
#include "pitches.h"
//pitches.h gives each note a frequency
int sariaPin = 0;
int eponaPin = 1;
int zeldaPin = 2;
int speakerPin = 11;
//set pin #s
int sariaMelody[] = {NOTE_F5, NOTE_A5, NOTE_B5, NOTE_F5, NOTE_A5, NOTE_B5, NOTE_F5, NOTE_A5,
                     NOTE_B5, NOTE_E6, NOTE_D6, NOTE_B5, NOTE_C6, NOTE_B5, NOTE_G5, NOTE_E5,
                     NOTE_D5, NOTE_E5, NOTE_G5, NOTE_E5
                    };
int eponaMelody[] = {NOTE_D6, NOTE_B5, NOTE_A5, 0, NOTE_D6, NOTE_B5, NOTE_A5, 0, NOTE_D6, NOTE_B5,
                     NOTE_A5, NOTE_B5, NOTE_A5
                    };
int zeldaMelody[] = {NOTE_E4, NOTE_G4, NOTE_D4, NOTE_C4, NOTE_D4,
                     NOTE_E4, NOTE_G4, NOTE_D4,   0,     NOTE_E4,
                     NOTE_G4, NOTE_D5, NOTE_C5, NOTE_G4, NOTE_F4,
                     NOTE_E4, NOTE_D4,    0,    NOTE_E4, NOTE_G4,
                     NOTE_D4, NOTE_C4, NOTE_D4, NOTE_E4, NOTE_G4,
                     NOTE_D4,    0,    NOTE_E4, NOTE_G4, NOTE_D5,
                     NOTE_C5, NOTE_G4
                    };
//set up melodies as arrays of notes
int sariaDurations[] = {4, 4, 2, 4, 4, 2, 4, 4, 4, 4, 2, 4, 4, 4, 4, 1, 4, 4, 4, 1};
int eponaDurations[] = {4, 4, 1, 16, 4, 4, 1, 16, 4, 4, 2, 2, 1};
int zeldaDurations[] = {2, 4, 2, 8, 8,
                        2, 4, 2, 4, 2,
                        4, 2, 4, 2, 8,
                        8, 2, 4,
                       };
//set up durations of each melody
const int threshold = 10;
//the minimum reading
void setup() {
}
void loop() {
  if (analogRead(sariaPin) > threshold) {
    for (int s = 0; s < 20; s++) {
      int sariaDuration = 1000 / sariaDurations[s];
      tone(speakerPin, sariaMelody[s], sariaDuration);
      int sariaPause = sariaDuration * .90;
      delay(sariaPause);
      noTone(speakerPin);
    }
  }
  else if (analogRead(eponaPin) > threshold) {
    for (int e = 0; e < 13; e++) {
      int eponaDuration = 1000 / eponaDurations[e];
      tone(speakerPin, eponaMelody[e], eponaDuration);
      int eponaPause = eponaDuration * 1.10;
      delay(eponaPause);
      noTone(speakerPin);
    }
  }
  else if (analogRead(zeldaPin) > threshold) {
    for (int z = 0; z < 18; z++) {
      int zeldaDuration = 1000 / zeldaDurations[z];
      tone(speakerPin, zeldaMelody[z], zeldaDuration);
      int zeldaPause = zeldaDuration * 1.30;
      delay(zeldaPause);
      noTone(speakerPin);
    }
  }
  /*if the reading at A0, A1, or A2 is higher than the threshold
  * for each note in the melody calculate its duration in seconds
  * play the note for that duration on the speaker pin
  * delay between each note (very small)
  * tone off
  */
}
