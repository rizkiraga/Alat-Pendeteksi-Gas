# Alat-Pendeteksi-Gas
## Apa itu Alarm Pendeteksi Gas?
Alarm pendeteksi gas adalah alat yang dapat mendeteksi adanya gas berbahaya di udara. Alarm ini biasanya digunakan untuk mencegah terjadinya kebakaran atau ledakan akibat kebocoran gas.
Alat dan Bahan
<br>
•	Arduino Uno
<br>
•	Kabel USB
<br>
•	Kabel jumper
<br>
•	Buzzer
<br>
•	LED
<br>
•	Breadboard
<br>
•	Sensor MQ2

## Cara Wiring Alarm Pendeteksi Gas
Berikut adalah langkah-langkah wiring alarm pendeteksi gas:
1.	Siapkan alat dan bahan yang diperlukan, yaitu:<br>
  •	Arduino Uno<br>
  •	Kabel USB<br>
  •	Kabel jumper<br>
  •	Buzzer<br>
  •	LED<br>
  •	Breadboard
2.	Hubungkan Arduino Uno ke komputer menggunakan kabel USB.
3.	Pasang sensor MQ2 pada breadboard.
4.	Hubungkan pin VCC sensor MQ2 ke pin 5V Arduino.
5.	Hubungkan pin GND sensor MQ2 ke pin GND Arduino.
6.	Hubungkan pin A0 sensor MQ2 ke pin A5 Arduino.
7.	Hubungkan pin positif buzzer ke pin 10 Arduino.
8.	Hubungkan pin negatif buzzer ke pin GND Arduino.
9.	Hubungkan pin positif LED merah ke pin 12 Arduino.
10.	Hubungkan pin negatif LED merah ke pin GND Arduino.
11.	Hubungkan pin positif LED hijau ke pin 11 Arduino.
12.	Hubungkan pin negatif LED hijau ke pin GND Arduino.

## Program
Program berikut akan menyalakan LED merah dan buzzer jika sensor MQ2 mendeteksi adanya gas dengan konsentrasi lebih dari 400 satuan.
```arduino
int redLed = 12;
int greenLed = 11;
int buzzer = 10;
int smokeA0 = A5;
// Nilai ambang batas
int sensorThres = 400;

void setup() {
  pinMode(redLed, OUTPUT);
  pinMode(greenLed, OUTPUT);
  pinMode(buzzer, OUTPUT);
  pinMode(smokeA0, INPUT);
  Serial.begin(9600);
}

void loop() {
  int analogSensor = analogRead(smokeA0);

  Serial.print("Pin A0: ");
  Serial.println(analogSensor);
  // Cek apakah telah mencapai nilai ambang batas
  if (analogSensor > sensorThres) {
    digitalWrite(redLed, HIGH);
    digitalWrite(greenLed, LOW);
    tone(buzzer, 1000, 200);
  } else {
    digitalWrite(redLed, LOW);
    digitalWrite(greenLed, HIGH);
    noTone(buzzer);
  }
  delay(100);
}
```

## Penjelasan Program
•	Pada fungsi setup(), kita menginisialisasi pin-pin Arduino sebagai output atau input.<br>
•	Pada fungsi loop(), kita membaca nilai sensor MQ2 menggunakan fungsi analogRead().<br>
•	Nilai sensor MQ2 kemudian dibandingkan dengan nilai ambang batas menggunakan operator >.<br>
•	Jika nilai sensor MQ2 lebih dari nilai ambang batas, maka LED merah dan buzzer akan menyala.<br>
•	Jika nilai sensor MQ2 tidak lebih dari nilai ambang batas, maka LED merah dan buzzer akan mati.<br>

## Cara Kerja Alarm Pendeteksi Gas
Alarm pendeteksi gas bekerja dengan cara mendeteksi perubahan konsentrasi gas di udara. Sensor MQ2 akan mengeluarkan sinyal analog yang besarnya tergantung pada konsentrasi gas di sekitarnya.
Pada program di atas, kita menggunakan nilai ambang batas 400. Artinya, alarm akan menyala jika konsentrasi gas di udara mencapai 400 satuan atau lebih.
Nilai ambang batas ini dapat disesuaikan dengan kebutuhan. Jika kita ingin alarm lebih sensitif, maka kita dapat menurunkan nilai ambang batas. Sebaliknya, jika kita ingin alarm kurang sensitif, maka kita dapat menaikkan nilai ambang batas.
