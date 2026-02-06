# gas-detection-alarm
it is the code of gas detection alarm by using esp8266 it detects gas based on threshold value given in code

// ESP8266 Gas Detection Alarm
// Sensor: MQ-2
// Board: NodeMCU ESP8266

#define GAS_SENSOR A0
#define BUZZER D5

int gasValue = 0;
int gasThreshold = 400;   // Adjust after calibration

void setup() {
  Serial.begin(9600);
  
  pinMode(GAS_SENSOR, INPUT);
  pinMode(BUZZER, OUTPUT);

  digitalWrite(BUZZER, LOW);

  Serial.println("Gas Detection System Started...");
}

void loop() {
  gasValue = analogRead(GAS_SENSOR);
  
  Serial.print("Gas Sensor Value: ");
  Serial.println(gasValue);

  if (gasValue > gasThreshold) {
    Serial.println(" GAS LEAK DETECTED!");
    digitalWrite(BUZZER, HIGH);
  } else {
    digitalWrite(BUZZER, LOW);
  }

  delay(1000);
}
